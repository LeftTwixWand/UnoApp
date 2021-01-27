## UnoApp
Sample Uno Platform project for demonstrating Uno Platform RequestedTheme bug.  
Repository is referencing to [this](https://github.com/unoplatform/uno/issues/5059) issue.

RequestedTheme works for application:
```XAML
<Application RequestedTheme="Dark" >
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="Themes/PurpleTheme.xaml"/>
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```
But not working with `UIElement`:
```XAML
<NavigationView RequestedTheme="Light">
    <NavigationView.Resources>
        <ResourceDictionary Source="Themes/PurpleTheme.xaml"/>
    </NavigationView.Resources>
</NavigationView>
```
