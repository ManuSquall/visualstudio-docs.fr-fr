---
title: Générer des applications Xamarin avec une interface utilisateur native dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 839ac68e7a27aa58907ddd653191f1b50f545671
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770330"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Générer des applications Xamarin avec une interface utilisateur native dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Une fois que vous avez effectué les étapes dans [Configurer et installer](../cross-platform/setup-and-install.md) et [Vérifier votre environnement Xamarin](../cross-platform/verify-your-xamarin-environment.md), cette procédure pas à pas vous montre comment générer une application Xamarin de base (ci-dessous) avec des couches d’IU (interface utilisateur) natives. Avec une IU native, le code partagé réside dans une bibliothèque de classes portable (PCL), et les projets de plateforme individuels contiennent les définitions d’IU.  
  
 ![Application Xamarin sur Android et Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "Build Xamarin multiplateforme 1")  
  
 Vous allez effectuer les opérations suivantes pour la générer :  
  
-   [Configurer votre solution](#solution)  
  
-   [Écrire le code de service de données partagé](#dataservice)  
  
-   [Concevoir une IU pour Android](#Android)  
  
-   [Concevoir une IU pour Windows Phone](#Windows)  
  
-   [Étapes suivantes](#next)  
  
> [!TIP]
>  Vous trouverez le code source complet de ce projet dans le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
> 
>   Si vous êtes confronté à des difficultés ou des erreurs, publiez vos questions sur [forums.xamarin.com](http://forums.xamarin.com). Vous pouvez résoudre de nombreuses erreurs en effectuant une mise à jour vers les derniers kits SDK nécessaires à Xamarin, comme indiqué dans les [notes de publication Xamarin](https://developer.xamarin.com/releases/) de chaque plateforme.    
> 
> [!NOTE]
>  La documentation du développeur Xamarin comporte également plusieurs procédures pas à pas, avec les sections de démarrage rapide (Quickstart) et d’exploration (Deep Dive) présentées ci-dessous : Dans chacune de ces pages, vérifiez que « Visual Studio » est sélectionné en haut à droite de la page pour afficher les procédures pas à pas s’appliquant à Visual Studio.  
> 
> - Applications Xamarin avec une interface utilisateur native :  
> 
>   -   [Hello, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (application simple avec un seul écran)  
>   -   [Hello, Android Multiscreen](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (application avec une navigation entre des écrans)  
>   -   [Android Fragments Walkthrough](http://developer.xamarin.com/guides/android/platform_features/fragments/fragments_walkthrough/) (utilisé entre autres choses pour des écrans maître/détails)  
>   -   [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)  
>   -   [Hello, iOS Multiscreen](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)  
>   -   Applications Xamarin avec Xamarin.Forms (interface utilisateur partagée)  
> 
>   -   [Hello, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)  
>   -   [Hello, Xamarin.Forms Multiscreen](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)  
  
##  <a name="solution"></a> Configurer votre solution  
 Les étapes suivantes permettent de créer une solution Xamarin avec une IU native, qui contient une bibliothèque PCL pour le code partagé et deux packages NuGet ajoutés.  
  
1. Dans Visual Studio, créez une solution **Application vide (native portable)** et nommez-la **WeatherApp**. Vous pouvez trouver plus facilement ce modèle en entrant **native portable** dans le champ de recherche.  
  
    S’il n’y figure pas, vous devez peut-être installer Xamarin ou activer la fonctionnalité Visual Studio 2015. Consultez [Setup and install](../cross-platform/setup-and-install.md).  
  
2. Après avoir cliqué sur OK pour créer la solution, vous avez un certain nombre de projets individuels :  
  
   - **WeatherApp (Portable)**: bibliothèque PCL où vous allez écrire du code qui est partagé entre les plateformes, notamment une logique métier commune et le code de l’interface utilisateur à l’aide de Xamarin.Forms.  
  
   - **WeatherApp.Droid**: projet qui contient le code Android natif. Ce projet est défini comme projet de démarrage par défaut.  
  
   - **WeatherApp.iOS**: projet qui contient le code iOS natif.  
  
   - **WeatherApp.WinPhone (Windows Phone 8.1)**: le projet qui contient le code Windows Phone natif.  
  
     Dans chaque projet natif, vous avez accès au concepteur natif pour la plateforme correspondante. Vous pouvez implémenter des écrans spécifiques à la plateforme.  
  
3. Ajoutez les packages NuGet et **Newtonsoft.Json** au projet de bibliothèque PCL, que vous allez utiliser pour traiter les informations récupérées à partir d’un service de données météo :  
  
   -   Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Solution ‘WeatherApp’**, puis sélectionnez **Gérer les packages NuGet pour la solution**.  
  
        Dans la fenêtre NuGet, sélectionnez l’onglet **Parcourir**, puis recherchez **Newtonsoft**.  
  
   -   Sélectionnez **Newtonsoft.Json**.  
  
   -   À droite de la fenêtre, cochez la case du projet **WeatherApp** (il s’agit du seul projet dans lequel vous devez installer le package).  
  
   -   Vérifiez que la valeur définie pour le champ **Version** est **Dernière stable** .  
  
   -   Cliquez sur **Installer**.  
  
   -   ![Localisation et installation du package NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
4. Répétez l’étape 3 ci-dessus pour rechercher et installer le package **Microsoft.Net.Http**.  
  
5. Générez votre solution et vérifiez l’absence d’erreur de génération.  
  
##  <a name="dataservice"></a> Écrire le code de service de données partagé  
 Le projet **WeatherApp (Portable)** est l’emplacement où vous allez écrire du code pour la bibliothèque PCL partagée entre les plateformes. La bibliothèque PCL est automatiquement incluse dans les packages d’application générés par les projets iOS, Android et Windows Phone.  
  
 Les étapes suivantes permettent d’ajouter du code à la bibliothèque PCL pour accéder aux données de ce service météo et stocker ces données :  
  
1.  Pour exécuter cet exemple, vous devez tout d’abord vous inscrire pour obtenir une clé API gratuite à l’adresse [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
2.  Cliquez avec le bouton droit sur le projet **WeatherApp** et sélectionnez **Ajouter > Classe**. Dans la boîte de dialogue **Ajouter un nouvel élément** , nommez le fichier **Weather.cs**. Vous utiliserez cette classe pour stocker les données du service de données météo.  
  
3.  Remplacez l’intégralité du contenu de **Weather.cs** par le code suivant :  
  
    ```csharp  
    namespace WeatherApp  
    {  
        public class Weather  
        {  
            public string Title { get; set; }  
            public string Temperature { get; set; }  
            public string Wind { get; set; }  
            public string Humidity { get; set; }  
            public string Visibility { get; set; }  
            public string Sunrise { get; set; }  
            public string Sunset { get; set; }  
  
            public Weather()  
            {  
                //Because labels bind to these values, set them to an empty string to  
                //ensure that the label appears on all platforms by default.  
                this.Title = " ";  
                this.Temperature = " ";  
                this.Wind = " ";  
                this.Humidity = " ";  
                this.Visibility = " ";  
                this.Sunrise = " ";  
                this.Sunset = " ";  
            }  
        }  
    }  
    ```  
  
4.  Ajoutez une autre classe au projet de bibliothèque PCL nommée **DataService.cs** que vous allez utiliser pour traiter les données JSON du service de données météo.  
  
5.  Remplacez l’intégralité du contenu de **DataService.cs** par le code suivant :  
  
    ```csharp  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
    using System.Net.Http;  
  
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
6.  Ajoutez une troisième classe à la bibliothèque PCL nommée **Core** , où vous allez placer la logique métier partagée, telle que la logique qui forme une chaîne de requête avec un code postal, appelle le service de données météo, puis remplit une instance de la classe **Weather** .  
  
7.  Remplacez le contenu de **Core.cs** par le code suivant :  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }
  
                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  Remplacez *VOTRE CLÉ ICI* dans le code par la clé API obtenue à l’étape 1 (elle doit être mise entre guillemets).  
  
9. Supprimez MyClass.cs dans la bibliothèque PCL, car nous n’allons pas l’utiliser.  
  
10. Générez le projet de bibliothèque PCL **WeatherApp** pour vérifier que le code est correct.  
  
##  <a name="Android"></a> Concevoir une IU pour Android  
 À présent, vous allez concevoir l’interface utilisateur, la connecter à votre code partagé, puis exécuter l’application.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Concevoir l'apparence de votre application  
  
1.  Dans l’**Explorateur de solutions**, développez le dossier **WeatherApp.Droid**>**Ressources**>**disposition**, puis ouvrez **Main.axml**. Le fichier s’ouvre dans le concepteur visuel. (Si une erreur liée à Java s’affiche, consultez ce [billet de blog](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)  
  
    > [!TIP]
    >  Le projet contient de nombreux autres fichiers. Ils ne sont pas abordés dans cette rubrique, mais si vous souhaitez étudier plus en détail la structure d’un projet Android, consultez [Part 2 Deep Dive](http://developer.xamarin.com/guides/android/getting_started/hello,android/hello,android_deepdive/) dans la rubrique Hello Android sur xamarin.com.  
  
2.  Sélectionnez et supprimez le bouton par défaut qui apparaît dans le concepteur.  
  
3.  Ouvrez la boîte à outils via **Affichage > Autres fenêtres > Boîte à outils**.  
  
4.  Dans la **Boîte à outils**, faites glisser un contrôle **RelativeLayout** sur le concepteur. Vous devez utiliser ce contrôle comme conteneur parent pour d’autres contrôles.  
  
    > [!TIP]
    >  Si, à un moment donné, la disposition ne semble pas correcte, enregistrez le fichier, puis passez de l’onglet **Création** à l’onglet **Source** pour actualiser l’affichage.  
  
5.  Dans la fenêtre **Propriétés**, affectez à la propriété **background** (dans le groupe Style) la valeur `#545454`.  
  
6.  Dans la **Boîte à outils**, faites glisser un contrôle **TextView** sur le contrôle **RelativeLayout** .  
  
7.  Dans la fenêtre **Propriétés**, définissez les propriétés suivantes (vous pouvez éventuellement trier la liste par ordre alphabétique à l’aide du bouton de tri situé dans la barre d’outils de la fenêtre Propriétés) :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**text**|**Search by Zip Code**|  
    |**ID**|`@+id/ZipCodeSearchLabel`|  
    |**layout_marginLeft**|`10dp`|  
    |**textColor**|`@android:color/white`|  
    |**textStyle**|`bold`|  
  
    > [!TIP]
    >  Notez que de nombreuses propriétés ne contiennent pas de liste déroulante de valeurs sélectionnables.  Il peut être difficile d’évaluer la valeur de chaîne à utiliser pour une propriété donnée. Pour obtenir des suggestions, essayez de rechercher le nom d’une propriété dans la page de la classe [R.attr](http://developer.android.com/reference/android/R.attr.html) .  
    >   
    >  De plus, une recherche rapide sur le web permet souvent d’accéder à une page à l’adresse [http://stackoverflow.com/](http://stackoverflow.com/) où d’autres personnes ont utilisé la même propriété.  
  
     À titre de référence, si vous passez en mode **Source**, vous devez voir le code suivant pour cet élément :  
  
    ```xml  
    <TextView  
        android:text="Search by Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:id="@+id/ZipCodeSearchLabel"  
        android:layout_centerVertical="true"  
        android:layout_marginLeft="10dp"  
        android:textColor="@android:color/white"  
        android:textStyle="bold" />  
  
    ```  
  
8.  À partir de la **Boîte à outils**, faites glisser un contrôle **TextView** sur le contrôle **RelativeLayout**, puis placez-le sous le contrôle ZipCodeSearchLabel. Pour ce faire, déposez le nouveau contrôle sur le bord approprié du contrôle existant. Pour vous faciliter la tâche, zoomez dans le concepteur.  
  
9. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**texte**|**Code postal**|  
    |**ID**|`@+id/ZipCodeLabel`|  
    |**layout_marginLeft**|`10dp`|  
    |**layout_marginTop**|`5dp`|  
  
     Le code en mode **Source** doit ressembler à ceci :  
  
    ```xml  
    <TextView  
        android:text="Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeSearchLabel"  
        android:id="@+id/ZipCodeLabel"  
        android:layout_marginTop="5dp"  
        android:layout_marginLeft="10dp" />  
    ```  
  
10. À partir de la **Boîte à outils**, faites glisser un contrôle **Number** sur **RelativeLayout**, placez-le sous l’étiquette **Zip Code**. Définissez ensuite les propriétés suivantes :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**ID**|`@+id/zipCodeEntry`|  
    |**layout_marginLeft**|`10dp`|  
    |**layout_marginBottom**|`10dp`|  
    |**width**|`165dp`|  
  
     Là encore, voici le code :  
  
    ```xml  
    <EditText  
        android:inputType="number"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeLabel"  
        android:id="@+id/zipCodeEntry"  
        android:layout_marginLeft="10dp"  
        android:layout_marginBottom="10dp"  
        android:width="165dp" />  
    ```  
  
11. À partir de la **Boîte à outils**, faites glisser un contrôle **Button** sur le contrôle **RelativeLayout**, puis placez-le à droite du contrôle zipCodeEntry. Définissez ensuite ces propriétés :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**ID**|`@+id/weatherBtn`|  
    |**texte**|**Obtenir la météo**|  
    |**layout_marginLeft**|`20dp`|  
    |**layout_alignBottom**|`@id/zipCodeEntry`|  
    |**width**|`165dp`|  
  
    ```xml  
    <Button    android:text="Get Weather"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_toRightOf="@id/zipCodeEntry"  
        android:id="@+id/weatherBtn"  
        android:layout_marginLeft="20dp"  
        android:layout_alignBottom="@id/zipCodeEntry"  
        android:width="165dp" />  
    ```  
  
12. Vous avez maintenant suffisamment d'expérience pour créer une interface utilisateur de base à l'aide du concepteur Android. Vous pouvez également créer une IU en ajoutant un balisage directement au fichier .asxml de la page. Pour créer le reste de l’IU de cette façon, passez en mode Source dans le concepteur, puis collez le balisage suivant *sous* la balise `</RelativeLayout>` (oui, sous la balise..., ces éléments ne sont pas inclus dans ReleativeLayout).  
  
    ```xml  
    <TextView  
            android:text="Location"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/locationLabel"  
            android:layout_marginLeft="10dp"  
            android:layout_marginTop="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/locationText"  
            android:layout_marginLeft="20dp"  
            android:layout_marginBottom="10dp" />  
        <TextView  
            android:text="Temperature"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/tempLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/tempText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Wind Speed"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/windLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/windText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Humidity"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/humidtyLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/humidityText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Visibility"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/visibilityLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/visibilityText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Time of Sunrise"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunriseLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunriseText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Time of Sunset"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunsetLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunsetText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
  
    ```  
  
13. Enregistrez le fichier, puis passez en mode **Design**. Votre interface utilisateur doit s'afficher comme suit :  
  
     ![Interface utilisateur pour application Android](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")  
  
14. Ouvrez **MainActivity.cs**, puis supprimez les lignes de la méthode *OnCreate* qui référencent le bouton par défaut supprimé précédemment. Une fois que vous avez terminé, le code doit ressembler à ceci :  
  
    ```  
    protected override void OnCreate (Bundle bundle)  
    {  
        base.OnCreate (bundle);  
  
        // Set our view from the "main" layout resource  
        SetContentView (Resource.Layout.Main);  
    }  
    ```  
  
15. Générez le projet Android pour vérifier votre travail. Notez que la génération entraîne l’ajout d’ID de contrôle au fichier **Resource.Designer.cs** pour que vous puissiez référencer les contrôles par leur nom dans le code.  
  
### <a name="consume-your-shared-code"></a>Consommer votre code partagé  
  
1.  Ouvrez le fichier **MainActivity.cs** du projet **WeatherApp** dans l’éditeur de code, puis remplacez son contenu par le code ci-dessous. Ce code appelle la méthode `GetWeather` que vous avez définie dans votre code partagé. Ensuite, dans l'interface utilisateur de l'application, il affiche les données qui sont récupérées à partir de cette méthode.  
  
    ```csharp  
    using System;  
    using Android.App;  
    using Android.Widget;  
    using Android.OS;  
  
    namespace WeatherApp.Droid  
    {  
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]  
        public class MainActivity : Activity  
        {  
            protected override void OnCreate(Bundle bundle)  
            {  
                base.OnCreate(bundle);  
  
                SetContentView(Resource.Layout.Main);  
  
                Button button = FindViewById<Button>(Resource.Id.weatherBtn);  
  
                button.Click += Button_Click;  
            }  
  
            private async void Button_Click(object sender, EventArgs e)  
            {  
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);  
  
                if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
                {  
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;  
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;  
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;  
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;  
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;  
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;  
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="run-the-app-and-see-how-it-looks"></a>Exécuter l'application pour vérifier son fonctionnement  
  
1.  Dans l’**Explorateur de solutions**, vérifiez que le projet **WeatherApp.Droid** est défini en tant que projet de démarrage.  
  
2.  Sélectionnez la cible de l’appareil ou de l’émulateur approprié, puis démarrez l’application en appuyant sur la touche F5.  
  
3.  Sur l’appareil ou dans l’émulateur, dans la zone d’édition, tapez un code postal valide pour les États-Unis (par exemple 60601), puis appuyez sur **Get Weather**. Les données météorologiques de cette région apparaissent ensuite dans les contrôles.  
  
     ![Application météo pour Android et Windows Phone](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")  
  
> [!TIP]
>  Le code source complet de ce projet se trouve dans le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
##  <a name="Windows"></a> Concevoir une IU pour Windows Phone  
 À présent, nous allons concevoir l’interface utilisateur pour Windows Phone, la connecter à votre code partagé, puis exécuter l’application.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Concevoir l'apparence de votre application  
 Le processus de conception de l’IU Windows Phone native dans une application Xamarin est le même que pour n’importe quelle application Windows Phone native. Nous n’entrerons donc pas dans les détails sur l’utilisation du concepteur. Pour cela, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
 À la place, il vous suffit d’ouvrir MainPage.xaml et de remplacer l’ensemble du code XAML par ce qui suit :  
  
```xaml  
<Page  
    x:Class="WeatherApp.WinPhone.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:WeatherApp.WinPhone"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d"  
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
  
    <Grid>  
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">  
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />  
        </StackPanel>  
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">  
  
            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>  
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>  
            <StackPanel Orientation="Horizontal">  
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />  
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>  
            </StackPanel>  
        </StackPanel>  
        <StackPanel Margin="10,175,0,0">  
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>  
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>  
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>  
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>  
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>  
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
        </StackPanel>  
    </Grid>  
</Page>  
```  
  
 Dans la vue de conception, votre interface utilisateur doit ressembler à ce qui suit :  
  
 ![Interface utilisateur d’application Windows Phone](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")  
  
### <a name="consume-your-shared-code"></a>Consommer votre code partagé  
  
1.  Dans le concepteur, sélectionnez le bouton **Obtenir la météo** .  
  
2.  Dans la fenêtre **Propriétés**, choisissez le bouton du gestionnaire d’événements (![Icône des gestionnaires d’événements Visual Studio](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")).  
  
     Cette icône figure dans l'angle supérieur de la fenêtre **Propriétés** .  
  
3.  À côté de l’événement **Click** , tapez **GetWeatherButton_Click**, puis appuyez sur la touche Entrée.  
  
     Cela génère un gestionnaire d'événements nommé `GetWeatherButton_Click`. L’éditeur de code s’ouvre et place votre curseur à l’intérieur du bloc de code de gestionnaire d’événements.  Remarque : Si l’éditeur ne s’ouvre pas quand vous appuyez sur ENTRÉE, double-cliquez simplement sur le nom de l’événement.  
  
4.  Remplacez ce gestionnaire d'événements par le code suivant.  
  
    ```csharp  
    private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            locationText.Text = weather.Title;  
            tempText.Text = weather.Temperature;  
            windText.Text = weather.Wind;  
            visibilityText.Text = weather.Visibility;  
            humidityText.Text = weather.Humidity;  
            sunriseText.Text = weather.Sunrise;  
            sunsetText.Text = weather.Sunset;  
  
            weatherBtn.Content = "Search Again";  
        }  
    }  
    ```  
  
     Ce code appelle la méthode `GetWeather` que vous avez définie dans votre code partagé. Il s'agit de la même méthode que celle que vous avez appelée dans votre application Android. Ce code montre aussi les données récupérées à partir de cette méthode dans les contrôles d'interface utilisateur de votre application.  
  
5.  Dans MainPage.xaml.cs, qui est ouvert, supprimez tout le code contenu dans la méthode **OnNavigatedTo**. Ce code servait simplement à gérer le bouton par défaut qui a été supprimé quand nous avons remplacé le contenu de MainPage.xaml.  
  
### <a name="run-the-app-and-see-how-it-looks"></a>Exécuter l'application pour vérifier son fonctionnement  
  
1.  Dans l’**Explorateur de solutions**, définissez le projet **WeatherApp.WinPhone** en tant que projet de démarrage.  
  
2.  Démarrez l'application en appuyant sur la touche F5.  
  
3.  Dans l’émulateur Windows Phone, dans la zone d’édition, tapez un code postal valide pour les États-Unis (par exemple 60601), puis appuyez sur **Get Weather**. Les données météorologiques de cette région apparaissent ensuite dans les contrôles.  
  
     ![Version Windows de l’application en cours d’exécution](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")  
  
> [!TIP]
>  Le code source complet de ce projet se trouve dans le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
##  <a name="next"></a> Étapes suivantes  
 **Ajouter une IU pour iOS à la solution**  
  
 Étendez cet exemple en ajoutant une IU native pour iOS. Pour cela, vous devez vous connecter à un Mac sur votre réseau local, où sont installés Xcode et Xamarin. Vous pourrez ensuite utiliser le concepteur iOS directement dans Visual Studio. Consultez le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) pour obtenir une application complète.  
  
 Consultez également la procédure pas à pas [Hello, iOS](http://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/hello,iOS_quickstart/) (xamarin.com). Vérifiez que « Visual Studio » est bien sélectionné en haut à droite des pages de xamarin.com pour que les instructions appropriées s’affichent.  
  
 **Ajouter du code spécifique à une plateforme dans un projet partagé**  
  
 Le code partagé d’une bibliothèque PCL est indépendant de la plateforme, car la bibliothèque PCL est compilée une seule fois et incluse dans chaque package de l’application spécifique à la plateforme. Si vous souhaitez écrire du code partagé qui utilise la compilation conditionnelle pour isoler le code spécifique à la plateforme, vous pouvez utiliser un projet *partagé*. Pour plus d’informations, consultez [Options de partage du code](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (xamarin.com).  
  
## <a name="see-also"></a>Voir aussi  
 [Site de développement Xamarin](http://developer.xamarin.com/)   
 [Centre de développement Windows](https://dev.windows.com/en-us)   
 [Affiche aide-mémoire pour Swift et C#](http://aka.ms/scposter)

