# How to bind and control the column properties on SfDataGrid using the MVVM pattern.

This article demonstrates how to bind and control the column properties on SfDataGrid.

To achieve this, a bindable property is exposed in the ViewModel. This property remains synchronized with the grid’s current selection and also updates the grid when its value changes from the ViewModel, ensuring two-way communication between the UI and the data layer.

## Xaml#:

```xml
<sfgrid:SfDataGrid
                ItemsSource="{Binding State}"
                AutoGenerateColumns="True">
                <sfgrid:SfDataGrid.Columns>
                    <sfgrid:GridTextColumn MappingName="Name" CellTextSize="{Binding TextSize}"/>
                </sfgrid:SfDataGrid.Columns>
</sfgrid:SfDataGrid>
```

## C#:

```C#
class ViewModel : INotifyPropertyChanged
{
    public double TextSize
    {
        get { return textSize; }
        set
        {
            textSize = value;
            OnPropertyChanged(nameof(TextSize));
        }
    }
}
```