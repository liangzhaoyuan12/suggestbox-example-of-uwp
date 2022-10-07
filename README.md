# suggestbox-example-of-uwp
suggestbox example of uwp

这里使用中文来写这个文档
声明：这个文档写来只是为了方便我自己记忆，当然，如果其他人有幸翻到这个项目应该也可以看得懂我在写什么

这里是对于uwp的搜索框的实例的记录

现在页面中加入<AutoSuggestBox Name="mysuggestbox" QueryIcon="Find" PlaceholderText="find something" TextChanged="mysuggestbox_TextChanged"/>
（当然，我把这个加进了page1页面中）
queryicon是图标；placeholdertext是占位字符；textchanged是在字符改变后触发的事件

在page1.cs中加入数组：string[] str = new string[] { "hello", "apple", "car","call","animal" ,"holiday" };

再在textchanged事件中加入以下
private void mysuggestbox_TextChanged(AutoSuggestBox sender, AutoSuggestBoxTextChangedEventArgs args)
        {
            var autosuggestbox = (AutoSuggestBox)sender;
            var filtered = str.Where(p => p.StartsWith(autosuggestbox.Text)).ToArray();
            autosuggestbox.ItemsSource = filtered;
        }
虽然我看不懂是什么意思，我甚至都没认真看过lambda语法和数组的where语法，所以现在只是记录下来方便以后写项目时直接取下来用
