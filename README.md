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


> Сергей Поздняков:
<Window x:Class="CarServiceApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Car Service App" Height="350" Width="525">
    <Grid>
        <TextBox x:Name="txtLastName" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="120"/>
        <TextBox x:Name="txtFirstName" HorizontalAlignment="Left" Height="23" Margin="10,40,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="120"/>
        <TextBox x:Name="txtPhoneNumber" HorizontalAlignment="Left" Height="23" Margin="10,70,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="120"/>
        <Button x:Name="btnAddOrder" Content="Добавить заказ" HorizontalAlignment="Left" Margin="10,100,0,0" VerticalAlignment="Top" Width="120" Click="AddOrder_Click"/>
        <Button x:Name="btnShowBuyers" Content="Показать клиентов" HorizontalAlignment="Left" Margin="10,130,0,0" VerticalAlignment="Top" Width="120" Click="ShowBuyers"/>
        <ListView x:Name="buyersListView" HorizontalAlignment="Left" Height="100" Margin="10,160,0,0" VerticalAlignment="Top" Width="500">
            <ListView.View>
                <GridView>
                    <GridViewColumn Header="ID" DisplayMemberBinding="{Binding Id}" Width="50"/>
                    <GridViewColumn Header="Фамилия" DisplayMemberBinding="{Binding LastName}" Width="150"/>
                    <GridViewColumn Header="Имя" DisplayMemberBinding="{Binding FirstName}" Width="150"/>
                    <GridViewColumn Header="Телефон" DisplayMemberBinding="{Binding PhoneNumber}" Width="150"/>
                </GridView>
            </ListView.View>
        </ListView>
    </Grid>
</Window>




КОД ПРОГРАММЫ




 



РАЗРАБОТЧИКИ

Этот проект был разработан и также будет дорабатываться студентами группы ИСП-8: Поздняков Сергей и Сибурёв Влад







