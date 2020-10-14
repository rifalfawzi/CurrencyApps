
#**CurrencyApps**

Aplikasi ini berfungsi sebagai perhitungan nilai tukar mata uang dari mata uang Rupiah Menjadi USD/Dollar

#**Fungsi**

- Sebagai kalkulator
- Mempermudah penghitungan

#**Cara Kerja**

Diawali dari method "MainWindow" pada class window.xaml.cs dideklarasikan dengan:

```csharp
private void Button_Hitung_Click(object sender, RoutedEventArgs e)
        {
            var nominalInput = InputTextBox.Text;
            var result = "invalid";
            if (currencyController.isAllowed(nominalInput))
            {
                result = currencyController.usdToIdr(nominalInput);
            }
            resultLabel.Content = result;
        }
```

logika perhitungan terdapat pada CurrencyController.cs sebagai berikut:
```csharp
 public string usdToIdr(string nominal)
        {
            var nominalDouble = Convert.ToDouble(nominal);
            var result = nominalDouble * 14680;
            return Convert.ToString(result);
        }

        public Boolean isAllowed(string nominal)
        {
            Regex regex = new Regex("[^0-9.-]+");
            return !regex.IsMatch(nominal);

        }
```

kita menggunakan regex agar ketika kita masukkan tulisan apa saja, maka ketika di pencet tombol hitung dia akan keluar kata invalid


**Terima Kasih**
