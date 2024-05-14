ОПИСАНИЕ ПРОЕКТА

Мы разработали программу автомастерской, которая регистрирует новые заказы клиентов. Информация о клиенте собирается следующая: фамилия, имя, отчество, номер телефона, марка машины, номер машины и регион (может быть пустым, если отсутствует номер), тип поломки, цена ремонта, статус ремонта.
Заполняющий данные (далее пользователь) должен добавлять данные, удалять, редактировать. 
При редактировании данных или удалении, пользователю должно отобразиться окно ввода пароля. При вводе правильного пароля, данные меняются, при вводе не правильного, данные не будут изменены. Подразумевается, что пароль знает только старший мастер.
Так же система должна иметь поиск по номеру машины или по ФИО клиента.

ИНТЕРФЕЙС ПРОЕКТА



![image](https://github.com/sergey675/WpfApp3/assets/161806606/738fa516-c565-4963-a1dd-f18219c8ad33)


![image](https://github.com/sergey675/WpfApp3/assets/161806606/ce058102-9238-4346-b2ee-7a83b36db106)


-Данное приложение предлагает пользователю внести свои данные в заказ: Пользователь с клавиатуры вводит свою фимилию , имя , телефон , марку авто и проблему которыю нужно решить.

-Далее пользователь должен нажать на кнопку "Добавить заказ" , который будет внесён в базу данных.

КОД ИНТЕРФЕЙСА






КОД ПРОГРАММЫ



using System;
using System.Windows;
using System.Data.SQLite;
using System.Collections.Generic;

namespace CarServiceApp
{
    public partial class MainWindow : Window
    {
        private SQLiteConnection _connection;
        public MainWindow()
        {
            InitializeComponent();
            InitializeDatabase();
        }
        private void InitializeDatabase()
        {
            _connection = new SQLiteConnection("Data Source=automasterry.db;Version=3;");
            _connection.Open();
            using (var cmd = new SQLiteCommand("CREATE TABLE IF NOT EXISTS Buyers (Id INTEGER PRIMARY KEY, LastName TEXT, FirstName TEXT, PhoneNumber TEXT)", _connection))
            {
                cmd.ExecuteNonQuery();
            }
        }
        private void AddBuyer(string lastName, string firstName, string phoneNumber)
        {
            using (var cmd = new SQLiteCommand("INSERT INTO Buyers (LastName, FirstName, PhoneNumber) VALUES (@LastName, @FirstName, @PhoneNumber)", _connection))
            {
                cmd.Parameters.AddWithValue("@LastName", lastName);
                cmd.Parameters.AddWithValue("@FirstName", firstName);
                cmd.Parameters.AddWithValue("@PhoneNumber", phoneNumber);
                cmd.ExecuteNonQuery();
            }
        }
        private void AddOrder_Click(object sender, RoutedEventArgs e)
        {
            string lastName = txtLastName.Text;
            string firstName = txtFirstName.Text;
            string phoneNumber = txtPhoneNumber.Text;
            using (var cmd = new SQLiteCommand("INSERT INTO Clients (LastName, FirstName, PhoneNumber) VALUES (@LastName, @FirstName, @PhoneNumber)", _connection))
            {
                cmd.Parameters.AddWithValue("@LastName", lastName);
                cmd.Parameters.AddWithValue("@FirstName", firstName);
                cmd.Parameters.AddWithValue("@PhoneNumber", phoneNumber);
                cmd.ExecuteNonQuery();
            }
            AddBuyer(lastName, firstName, phoneNumber);
            MessageBox.Show("Заказ успешно добавлен!");
        }
        private void ShowBuyers(object sender, RoutedEventArgs e)
        {
            using (var cmd = new SQLiteCommand("SELECT * FROM Buyers", _connection))
            {
                using (SQLiteDataReader reader = cmd.ExecuteReader())
                {
                    List<Buyer> buyers = new List<Buyer>();
                    while (reader.Read())
                    {
                        buyers.Add(new Buyer
                        {
                            Id = reader.GetInt32(0),
                            LastName = reader.GetString(1),
                            FirstName = reader.GetString(2),
                            PhoneNumber = reader.GetString(3)
                        });
                    }
                    buyersListView.ItemsSource = buyers;
                }
            }
        }

        public class Buyer
        {
            public int Id { get; set; }
            public string LastName { get; set; }
            public string FirstName { get; set; }
            public string PhoneNumber { get; set; }
        }
    }
}
 



РАЗРАБОТЧИКИ

Этот проект был разработан и также будет дорабатываться студентами группы ИСП-8: Поздняков Сергей и Сибурёв Влад







