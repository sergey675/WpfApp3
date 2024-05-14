ОПИСАНИЕ ПРОЕКТА

Мы разработали программу автомастерской, которая регистрирует новые заказы клиентов. Информация о клиенте собирается следующая: фамилия, имя, отчество, номер телефона, марка машины, номер машины и регион (может быть пустым, если отсутствует номер), тип поломки, цена ремонта, статус ремонта.
Заполняющий данные (далее пользователь) должен добавлять данные, удалять, редактировать. 
При редактировании данных или удалении, пользователю должно отобразиться окно ввода пароля. При вводе правильного пароля, данные меняются, при вводе не правильного, данные не будут изменены. Подразумевается, что пароль знает только старший мастер.
Так же система должна иметь поиск по номеру машины или по ФИО клиента.

ИНТЕРФЕЙС ПРОЕКТА



![image](https://github.com/sergey675/WpfApp3/assets/161806606/738fa516-c565-4963-a1dd-f18219c8ad33)
-Данное приложение предлагает пользователю внести свои данные в заказ: Пользователь с клавиатуры вводит свою фимилию , имя , телефон , марку авто и проблему которыю нужно решить.
-Далее пользователь должен нажать на кнопку "Добавить заказ" , который будет внесён в базу данных.

КОД ИНТЕРФЕЙСА
<Window x:Class="WPFApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Product Viewer" Height="450" Width="800">
    <Grid>
        <StackPanel Orientation="Horizontal" HorizontalAlignment="Center" VerticalAlignment="Top" Margin="0,10,0,0">
            <Button Content="Phones" Click="ShowPhones" Margin="5"/>
            <Button Content="Headphones" Click="ShowHeadphones" Margin="5"/>
            <Button Content="Tablets" Click="ShowTablets" Margin="5"/>
            <Button Content="All Categories" Click="ShowAllCategories" Margin="5"/>
        </StackPanel>
        <ListView x:Name="productsListView" HorizontalAlignment="Center" VerticalAlignment="Center" Margin="0,50,0,0">
            <ListV>
                <GridView>
                    <GridViewColumn Header="Name" DisplayMemberBinding="{Binding Name}"/>
                    <GridViewColumn Header="Manufacturer" DisplayMemberBinding="{Binding Manufacturer}"/>
                    <GridViewColumn Header="Warranty" DisplayMemberBinding="{Binding Warranty}"/>
                    <GridViewColumn Header="Price" DisplayMemberBinding="{Binding Price}"/>
                </GridView>
            </ListV<Window x:Class="CarServiceApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Car Service App" Height="350" Width="525">
            <Grid>
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto"/>
                    <RowDefinition Height="Auto"/>
                    <RowDefinition Height="Auto"/>
                    <RowDefinition Height="Auto"/>
                    <RowDefinition Height="Auto"/>
                    <RowDefinition Height="Auto"/>
                </Grid.RowDefinitions>

                <TextBlock Grid.Row="0" Text="Фамилия:"/>
                <TextBox x:Name="txtLastName" Grid.Row="0" Width="200"/>

                <TextBlock Grid.Row="1" Text="Имя:"/>
                <TextBox x:Name="txtFirstName" Grid.Row="1" Width="200"/>

                <TextBlock Grid.Row="2" Text="Телефон:"/>
                <TextBox x:Name="txtPhoneNumber" Grid.Row="2" Width="200"/>

                <TextBlock Grid.Row="3" Text="Марка авто:"/>
                <TextBox x:Name="txtCarMake" Grid.Row="3" Width="200"/>

                <TextBlock Grid.Row="4" Text="Проблема:"/>
                <TextBox x:Name="txtIssueType" Grid.Row="4" Width="200"/>

                <Button Grid.Row="5" Content="Добавить заказ" Click="AddOrder_Click" Width="100"/>
            </Grid>
</Window> iew.View>
        </ListView>
    </Grid>
</Window>
КОД ПРОГРАММЫ
using System;
using System.Windows;

namespace CarServiceApp
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void AddOrder_Click(object sender, RoutedEventArgs e)
        {
            string lastName = txtLastName.Text;
            string firstName = txtFirstName.Text;
            string phoneNumber = txtPhoneNumber.Text;
            string carMake = txtCarMake.Text;
            string issueType = txtIssueType.Text;



            MessageBox.Show("Заказ успешно добавлен!");
        }
    }
}




РАЗРАБОТЧИКИ

Этот проект был разработан и также будет дорабатываться студентами группы ИСП-8: Поздняков Сергей и Сибурёв Влад







