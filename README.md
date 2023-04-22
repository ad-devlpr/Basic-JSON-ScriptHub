# JSON-ScriptHub

**MAKE SURE TO GIVE CREDITS TO ME AND PareX IF YOU'RE USING THIS!!!**

Credits:
PareX - Documentation ;
Me/Ad - Everything other than that. Also made modifications to the documentation (was outdated, updated it recently).

A free to use JSON script-hub that you can use for your exploit!

This gets updated constantly and I myself use this for my sploits.

To import it into your exploit, Please read the documentation provided.
You may or may not give credits to me!

#### Documentation
Please use the documentation given to import this scripthub into your exploit.
First, Add the following to your scripthub window:
```diff
-A listbox
-A richtextbox
-A button
-Newtonsoft.Json (NuGet package or DLL [REFERENCE])

(To install Newtonsoft.Json via NuGet; In your visual studio with the current project open, Go to Project > Manage NuGet Packages > Browse. Once you're
there, Search for "Newtonsoft.Json" in it and install it. Then, In your scripthub window's code, At the top, Put this: )
```
Once you have all of them, Use the code below to import the scripthub into your exploit. (FULL CREDITS TO PareX FOR THE CODE)

Put this outside of any void or other func (Eg: Under  public partial class Form)
```csharp
private readonly string jsonLink = "https://raw.githubusercontent.com/AlexDev1289/JSON-ScriptHub/main/JSON-ScriptHub.json";
```

Then, Put this under your Form_Load or Under InitializeComponent()
```csharp
var json_object = JObject.Parse(new WebClient().DownloadString(jsonLink))["scriptHub"];
            foreach (JToken sub_object in json_object.Children())
                listBox2.Items.Add($"{json_object[sub_object.ToObject<JProperty>().Name]["Name"]}");
```

After that is done, Double-Click the listbox and put this code in it
```csharp
var json_object = JObject.Parse(new WebClient().DownloadString(jsonLink))["scriptHub"];
            foreach (JToken sub_object in json_object.Children())
            {
                if (json_object[sub_object.ToObject<JProperty>().Name]["Name"].ToString() == listBox2.SelectedItem.ToString())
                {
                    richTextBox1.Text = json_object[sub_object.ToObject<JProperty>().Name]["Description"].ToString();
                }
            }
```

We've finished initializing everything except the execute button, Hence we will do it now.
Please use the code below for the execute button.
```csharp
if (listBox1.SelectedItem is null) return;
                var json_object = JObject.Parse(new WebClient().DownloadString(jsonLink))["scriptHub"];
                foreach (JToken sub_object in json_object.Children())
                {
                    if (json_object[sub_object.ToObject<JProperty>().Name]["Name"].ToString() == listBox2.SelectedItem.ToString())
                    {
                        YourAPI_OR_DLL.Execute(json_object[sub_object.ToObject<JProperty>().Name]["source"].ToString());
                    }

                }
```
Make sure to change the "YourAPI_OR_DLL.Execute func to literally your API or Dll's execute function!

--------------------------------------------------------------------------------------------------------------

Congratulations! You've successfully finished importing/making the scripthub!
I will be updating the scripthub with new scripts whenever I can.

If you are looking forward to make your own JSON script hub, Don't hesitate to use the format from Dont_Mind_This.txt to make your own JSON scripthub with custom scripts.

DM Ad#1085 if you need help / having issues in doing this.

Thank you!
See you,
Ad.
