## UnoApp
Sample Uno Platform project for demonstrating `Uno.Microsoft.Toolkit.Uwp.UI.Controls` error.  
Repository is referencing to [this](https://github.com/unoplatform/uno/issues/4708) issue.

All the projects (**UWP**, **Skia.Gtk** and **macOS**) are using this package:  
`Uno.Microsoft.Toolkit.Uwp.UI.Controls` version `6.1.0-build.201.gdd585882df`

I'm trying to use BitmatIcon as NavigationViewItem.Icon:
```XAML
<NavigationView>
        <NavigationView.MenuItems>
            <NavigationViewItem Content="My item">
                <NavigationViewItem.Icon>
                    <BitmapIcon ShowAsMonochrome="False" Height="16" Width="16" UriSource="ms-appx:///Assets/bender.png"/>
                </NavigationViewItem.Icon>
            </NavigationViewItem>
        </NavigationView.MenuItems>
    </NavigationView>
```

With **UWP** project it works normal, but for **Linux** and **Mac** I've got this error:  
`BitmapIcon doesn't contains definition for 'UriSource' (CS0117)`

I suppose, that linker is going to use `Uno.Microsoft.Toolkit.Uwp.UI.Controls` instead `Uno.UI`.

## How to solve it?
There are few ways:
 - Don't use `Uno.Microsoft.Toolkit.Uwp.UI.Controls`
 - Add straight reference to BitmapIcon:
```XAML
<Windows.UI.Xaml.Controls.BitmapIcon UriSource="..."/>
```
It will be working for **Linux** and **Mac**, but the second decision will be conflict with **UWP** project, because namespace `Windows.UI.Xaml.Controls` is using by default, and linker understand it as:  
`Windows.UI.Xaml.Controls.Windows.UI.Xaml.Controls.BitmapIcon`
