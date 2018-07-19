---
title: Générer des applications Xamarin avec une interface utilisateur native dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 1b70ea2cc12530065b2a297e54ff494bcc765c9c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757251"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Créer des applications Xamarin avec une interface utilisateur native dans Visual Studio

La plupart des développeurs qui choisissent Xamarin et C# pour écrire des applications mobiles multiplateformes utilisent Xamarin.Forms. Xamarin.Forms définit une interface utilisateur qui correspond à des contrôles natifs dans iOS, Android et la plateforme Windows universelle (UWP). Xamarin.Forms est décrit dans l’article [Principes fondamentaux de la création d’applications avec Xamarin.Forms dans Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

Cet article décrit une approche différente qui implique l’accès aux API natives de l’interface utilisateur de chaque plateforme. L’utilisation des API natives est une approche beaucoup plus difficile que Xamarin.Forms, car elle nécessite des connaissances approfondies de chaque plateforme. L’avantage est que vous pouvez adapter l’interface utilisateur aux forces et fonctionnalités propres à chaque plateforme, tout en partageant toujours une logique métier sous-jacente.

Une fois que vous avez effectué les étapes dans [Configurer et installer](../cross-platform/setup-and-install.md) et [Vérifier votre environnement Xamarin](../cross-platform/verify-your-xamarin-environment.md), cette procédure pas à pas vous montre comment générer une application Xamarin de base avec des couches d’interface utilisateur native. Avec une interface utilisateur native, le code partagé réside dans une bibliothèque .NET Standard et les projets de plateforme individuels contiennent les définitions d’interface utilisateur. Voici l’application que vous allez générer en cours d’exécution (de gauche à droite) sur les téléphones iOS et Android ainsi que le bureau Windows 10.

![Application Xamarin sur iOS, Android et Windows](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)

Vous allez effectuer les opérations suivantes pour la générer :

- [Configurer votre solution](#solution)

- [Écrire le code de service de données partagé](#dataservice)

- [Concevoir une IU pour Android](#Android)

- [Concevoir une interface utilisateur pour Windows](#Windows)

- [Étapes suivantes](#next), avec la conception d’une interface utilisateur iOS

> [!TIP]
> Vous trouverez le code source complet de ce projet dans le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Si vous êtes confronté à des difficultés ou des erreurs, publiez vos questions sur [forums.xamarin.com](http://forums.xamarin.com). Vous pouvez résoudre de nombreuses erreurs en effectuant une mise à jour vers les derniers kits SDK nécessaires à Xamarin, comme indiqué dans les [notes de publication Xamarin](https://developer.xamarin.com/releases/) de chaque plateforme.

> [!NOTE]
> La documentation du développeur Xamarin comporte également plusieurs procédures pas à pas, avec les sections de démarrage rapide (Quickstart) et d’approfondissement (Deep Dive) présentées ci-dessous : Dans chacune de ces pages, vérifiez que « Visual Studio » est sélectionné pour afficher les procédures pas à pas s’appliquant à Visual Studio.
>
>  -   Applications Xamarin avec une interface utilisateur native :
>     -   [Hello, Android](/xamarin/android/get-started/hello-android/) (application simple avec un seul écran)
>     -   [Hello, Android Multiscreen](/xamarin/android/get-started/hello-android-multiscreen/) (application avec une navigation entre des écrans)
>     -   [Android Fragments Walkthrough](/xamarin/android/platform/fragments/implementing-with-fragments/) (utilisé entre autres choses pour des écrans maître/détails)
>     -   [Hello, iOS](/xamarin/ios/get-started/hello-iOS/)
>     -   [Hello, iOS Multiscreen](/xamarin/ios/get-started/hello-iOS-multiscreen/)

>  -   Applications Xamarin avec Xamarin.Forms (interface utilisateur partagée)
>     -   [Hello, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)
>     -   [Hello, Xamarin.Forms Multiscreen](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)

<a name="solution" />

##  <a name="set-up-your-solution"></a>Configurer votre solution

Visual Studio n’a pas de modèle de solution pour la création d’applications d’interface utilisateur natives partageant une bibliothèque .NET Standard. Toutefois, il n’est pas difficile de générer une telle solution à partir des projets individuels. Les étapes suivantes permettent de créer une solution Xamarin avec des projets pour chaque type de plateforme d’application et une bibliothèque .NET Standard pour le code partagé.

1.  Dans Visual Studio, créez une solution **Bibliothèque de classes (.NET Standard)** et nommez-la **WeatherApp**. Vous pouvez trouver plus facilement ce modèle en sélectionnant **Visual C#** à gauche, puis **.NET Standard** :

    ![Création d’une solution .NET Standard](../cross-platform/media/cross-plat-xamarin-build-2.png)

    Après avoir cliqué sur OK, la solution **WeatherApp** se compose d’un seul projet nommé **WeatherApp**.

2.  Si vous souhaitez cibler iOS, ajoutez un projet iOS à la solution. Cliquez avec le bouton droit sur le nom de la solution dans **l’Explorateur de solutions**, puis sélectionnez **Ajouter** et **Nouveau projet**.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez à gauche **Visual C#**, puis **iOS** et **Universel**. (Si cette option n’y figure pas, vous devez peut-être installer Xamarin ou activer la fonctionnalité Visual Studio 2017. Consultez [Configurer et installer](../cross-platform/setup-and-install.md).) Dans la liste des modèles, sélectionnez **Application avec affichage unique (iOS)**. Affectez-lui le nom **WeatherApp.iOS**.

3.  Si vous souhaitez cibler Android, ajoutez un projet Android à la solution. Dans la boîte de dialogue **Nouveau projet**, sélectionnez à gauche **Visual C#**, puis **Android**. Dans la liste des modèles, sélectionnez **Application vide (Android)**. Affectez-lui le nom **WeatherApp.Android**.

4. Si vous souhaitez cibler la plateforme Windows universelle, dans la boîte de dialogue **Nouveau projet**, sélectionnez à gauche **Visual C#**, puis **Windows universel**. Dans la liste des modèles, sélectionnez **Application vide (Windows universel)** et affectez-lui le nom **WeatherApp.UWP**.

5. Pour chacun des projets d’application (iOS, Android et UWP), cliquez avec le bouton droit sur la section **Références** dans **l’Explorateur de solutions** et sélectionnez **Ajouter une référence**. Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez à gauche **Projet** et **Solution**. Vous verrez une liste de tous les projets de la solution à l’exception du projet dont vous gérez les références :

   ![Définition d’une référence au projet .NET Standard](../cross-platform/media/cross-plat-xamarin-build-3.png)

   Cochez la case en regard de **WeatherApp**.

   Une fois que vous avez coché cette case pour chacun des projets d’application, tous les projets contiennent des références à la bibliothèque .NET Standard et peuvent partager le code dans cette bibliothèque.

6. Ajoutez le package NuGet **Newtonsoft.Json** au projet .NET Standard, que vous allez utiliser pour traiter les informations récupérées à partir d’un service de données météo :

    -   Cliquez avec le bouton droit sur le projet **WeatherApp** dans **l’Explorateur de solutions** et sélectionnez **Gérer les packages NuGet...**.

         Dans la fenêtre NuGet, sélectionnez l’onglet **Parcourir**, puis recherchez **Newtonsoft**.

    -   Sélectionnez **Newtonsoft.Json**.

    -   Vérifiez que la valeur définie pour le champ **Version** est **Dernière stable** .

    -   Cliquez sur **Installer**.

7.  Répétez l’étape 6 pour rechercher et installer le package **Microsoft.CSharp** dans le projet .NET Standard. Cette bibliothèque est nécessaire pour utiliser le type de données `dynamic` C# dans une bibliothèque .NET Standard.

8.  Générez votre solution et vérifiez l’absence d’erreur de génération.

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Écrire le code de service de données partagé

 Le projet **WeatherApp** est la bibliothèque .NET Standard. Ce projet représente l’emplacement où vous allez écrire du code qui est partagé entre toutes les plateformes. Comme chaque projet d’application a une référence à la bibliothèque .NET Standard, la bibliothèque est comprise dans les packages d’application iOS, Android et UWP.

 Les étapes suivantes permettent d’ajouter du code à la bibliothèque .NET Standard pour accéder aux données de ce service météo et stocker ces données :

1.  Vous devez tout d’abord vous inscrire pour obtenir une clé API météo gratuite sur [http://openweathermap.org/appid](http://openweathermap.org/appid). Cette clé API permet à l’application d’obtenir la météo pour n’importe quel code postal des États-Unis. (Elle ne fonctionne pas pour les codes postaux en dehors des États-Unis.)

2.  Cliquez avec le bouton droit sur le projet **WeatherApp** et sélectionnez **Ajouter > Classe**. Dans la boîte de dialogue **Ajouter un nouvel élément** , nommez le fichier **Weather.cs**. Vous allez utiliser cette classe pour stocker les données du service de données météo.

3.  Remplacez l’intégralité du contenu de **Weather.cs** par le code suivant :

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```

4.  Ajoutez au projet .NET Standard une autre classe nommée **DataService.cs**. Vous allez utiliser cette classe pour traiter les données JSON du service de données météo.

5.  Remplacez l’intégralité du contenu de **DataService.cs** par le code suivant :

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> GetDataFromService(string queryString)
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

6.  Ajoutez à la bibliothèque .NET Standard une troisième classe nommée **Core.cs**. Vous allez utiliser cette classe pour former une chaîne de requête avec un code postal, appeler le service météo, puis remplir une instance de la classe **Weather**.

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
                string key = "YOUR API KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);

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

8. Remplacez la première occurrence de *YOUR API KEY HERE* par la clé API que vous avez obtenue à l’étape 1. Les guillemets sont toujours nécessaires.

9. Supprimez **MyClass.cs** de la bibliothèque .NET Standard, car elle ne sera pas utilisée.

10. Générez le projet **WeatherApp** pour vérifier que le code est correct.

<a name="Android" />

## <a name="design-ui-for-android"></a>Concevoir une interface utilisateur pour Android

 À présent, vous pouvez concevoir l’interface utilisateur, la connecter à votre code partagé, puis exécuter l’application.

### <a name="design-the-look-and-feel-of-your-app"></a>Concevoir l'apparence de votre application

1.  Dans **l’Explorateur de solutions**, développez le dossier **WeatherApp.Droid > Ressources > disposition**, puis ouvrez **Main.axml**. Cette commande ouvre le fichier dans le concepteur visuel. (Si une erreur liée à Java s’affiche, consultez ce [billet de blog](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    >  Le projet contient de nombreux autres fichiers. Ils ne sont pas abordés dans cet article, mais si vous souhaitez étudier plus en détail la structure d’un projet Android, consultez [Part 2 Deep Dive](/xamarin/android/get-started/hello-android/hello-android-deepdive/) dans l’article Hello Android.

2.  Ouvrez la boîte à outils via **Affichage > Autres fenêtres > Boîte à outils**.

3.  Dans la **Boîte à outils**, faites glisser un contrôle **RelativeLayout** sur le concepteur. Vous devez utiliser ce contrôle comme conteneur parent pour d’autres contrôles.

    > [!TIP]
    >  Si, à un moment donné, la disposition ne semble pas correcte, enregistrez le fichier, puis passez de l’onglet **Création** à l’onglet **Source** pour actualiser l’affichage.

4.  Dans la fenêtre **Propriétés**, affectez à la propriété **background** (dans le groupe Style) la valeur `#545454`.  Vérifiez dans le titre de la fenêtre **Propriétés** que vous définissez l’arrière-plan du contrôle **RelativeLayout**.

5.  Dans la **Boîte à outils**, faites glisser un contrôle **TextView** sur le contrôle **RelativeLayout** .

6.  Dans la fenêtre **Propriétés**, définissez les propriétés suivantes. (Vous pouvez éventuellement trier la liste par ordre alphabétique à l’aide du bouton de tri situé dans la barre d’outils de la fenêtre Propriétés.)

    |Property|Value|
    |--------------|-----------|
    |**text**|**Search by Zip Code**|
    |**ID**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginStart**|`10dp`|
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
        android:layout_marginStart="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

7.  À partir de la **Boîte à outils**, faites glisser un contrôle **TextView** sur le contrôle **RelativeLayout**, puis placez-le sous le contrôle ZipCodeSearchLabel. Déposez le nouveau contrôle sur le bord approprié du contrôle existant. Pour vous faciliter la tâche, effectuez un zoom dans le concepteur afin de positionner le contrôle.

8. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes :

    |Propriété|Value|
    |--------------|-----------|
    |**texte**|**Code postal**|
    |**ID**|`@+id/ZipCodeLabel`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginTop**|`6dp`|
    |**textColor**|`@android:color/white`|

    Le code en mode **Source** doit ressembler à ceci :

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"
        android:textColor="@android:color/white" />
    ```

9. À partir de la **Boîte à outils**, faites glisser un contrôle **Number** sur **RelativeLayout**, placez-le sous l’étiquette **Zip Code**. Définissez ensuite les propriétés suivantes :

    |Property|Value|
    |--------------|-----------|
    |**ID**|`@+id/zipCodeEntry`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**width**|`165dp`|
    |**textColor**|`@android:color/white`|

    Le contrôle **Number** représente l’emplacement où l’utilisateur tape un code postal à cinq chiffres des États-Unis. Voici le balisage qui correspond à ce contrôle :

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginStart="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp"
        android:textColor="@android:color/white" />
    ```

10. À partir de la **Boîte à outils**, faites glisser un contrôle **Button** sur le contrôle **RelativeLayout**, puis placez-le à droite du contrôle zipCodeEntry. Définissez ensuite ces propriétés :

    |Property|Value|
    |--------------|-----------|
    |**ID**|`@+id/weatherBtn`|
    |**texte**|**Obtenir la météo**|
    |**layout_marginStart**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**width**|`165dp`|

    ```xml
    <Button
        android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginStart="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

11. Vous avez maintenant suffisamment de connaissances pour générer une interface utilisateur de base à l’aide du concepteur Android. Vous pouvez également créer une interface utilisateur en ajoutant un balisage directement au fichier Main.axml de la page. Pour créer le reste de l’interface utilisateur de cette façon, passez en mode Source dans le concepteur, puis collez le balisage suivant *sous* la balise de fin `</RelativeLayout>`. (Ces éléments doivent être sous la balise, car il ne sont *pas* inclus dans le contrôle `RelativeLayout`.)

    ```xml
    <TextView
        android:text="Location"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationText"
        android:layout_marginStart="20dp"
        android:layout_marginBottom="10dp" />
    <TextView
        android:text="Temperature"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Wind Speed"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Humidity"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidtyLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Visibility"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunrise"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunset"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    ```

12. Enregistrez le fichier, puis passez en mode **Design**. Votre interface utilisateur doit s'afficher comme suit :

     ![Interface utilisateur pour application Android](../cross-platform/media/xamarin_androidui.png)

13. Ouvrez **MainActivity.cs**. Le code doit ressembler à ceci :

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

14. Générez le projet Android pour vérifier votre travail. Le processus de génération ajoute les ID des contrôles au fichier **Resource.Designer.cs** pour que vous puissiez y faire référence par leur nom dans le code.

### <a name="consume-your-shared-code"></a>Consommer votre code partagé

1.  Ouvrez le fichier **MainActivity.cs** du projet **WeatherApp** dans l’éditeur de code, puis remplacez son contenu par le code ci-dessous. Ce code appelle la méthode `GetWeather` que vous avez définie dans votre code partagé. Ensuite, dans l'interface utilisateur de l'application, il affiche les données qui sont récupérées à partir de cette méthode.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App",
                  Theme = "@android:style/Theme.Material.Light",
                  MainLauncher = true)]
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

    Notez que l’activité a reçu un thème pour un arrière-plan clair.

### <a name="run-the-app-and-see-how-it-looks"></a>Exécuter l'application pour vérifier son fonctionnement

1.  Dans l’**Explorateur de solutions**, vérifiez que le projet **WeatherApp.Droid** est défini en tant que projet de démarrage.

2.  Sélectionnez la cible de l’appareil ou de l’émulateur approprié, puis démarrez l’application en appuyant sur la touche F5.

    > [!NOTE]
    > Si Visual Studio indique que le projet Android ne peut pas trouver le fichier Newtonsoft.Json, ajoutez ce package NuGet au projet Android.

3.  Sur l’appareil ou dans l’émulateur, tapez un code postal à cinq chiffres des États-Unis valide dans la zone d’édition et appuyez sur **Obtenir la météo**. Les données météorologiques de cette région apparaissent ensuite dans les contrôles.

    [![Application Xamarin sur Android](../cross-platform/media/cross-plat-xamarin-build-1-android.png)](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)

> [!TIP]
>  Le code source complet de ce projet se trouve dans le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="Windows" />

## <a name="design-ui-for-windows"></a>Concevoir une interface utilisateur pour Windows

L’étape suivante consiste à concevoir l’interface utilisateur pour Windows, la connecter à votre code partagé, puis exécuter l’application.

### <a name="design-the-look-and-feel-of-your-app"></a>Concevoir l'apparence de votre application

 Le processus de conception d’une interface utilisateur UWP native dans une application Xamarin est le même que pour n’importe quelle autre application UWP native. Nous n’entrerons donc pas dans les détails sur l’utilisation du concepteur. Pour obtenir une présentation détaillée, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 Au lieu de cela, ouvrez **MainPage.xaml** et remplacez l’intégralité du contenu XAML par le balisage suivant :

```xaml
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="120" Margin="10,40,0,0" Width="400"
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap"
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />

            <TextBlock Text="Zip Code" TextWrapping="Wrap"
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>

            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text=""
                         Margin="10,10,0,0" VerticalAlignment="Top"
                         InputScope="Number" Width="165" />

                <Button x:Name="weatherBtn" Content="Get Weather"
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60"
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>

        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>

                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>

            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />

            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />

            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```

### <a name="consume-your-shared-code"></a>Consommer votre code partagé

Dans le fichier code-behind **MainPage.xaml.cs**, ajoutez le gestionnaire d’événements suivant pour le bouton :

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

Ce code appelle la méthode `GetWeather` que vous avez définie dans votre code partagé. La méthode `GetWeather` est la même que celle que vous avez appelée dans votre application Android. Ce code montre aussi les données récupérées à partir de cette méthode dans les contrôles d'interface utilisateur de votre application.

### <a name="run-the-app-and-see-how-it-looks"></a>Exécuter l'application pour vérifier son fonctionnement

1.  Dans **l’Explorateur de solutions**, définissez le projet **WeatherApp.UWP** comme projet de démarrage.

2.  Dans la zone de liste déroulante **Plateformes solution**, sélectionnez **x86** et **Ordinateur local** pour déployer l’application sur le bureau Windows 10.

3.  Démarrez l'application en appuyant sur la touche F5.

4.  Tapez un code postal à cinq chiffres des États-Unis valide dans la zone d’édition et appuyez sur **Obtenir la météo**. Les données météo de cette région apparaissent ensuite dans la page.

    [![Application Xamarin sur UWP](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png)](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)

> [!TIP]
>  Le code source complet de ce projet se trouve dans le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="next" />

## <a name="next-steps"></a>Étapes suivantes

 **Ajouter une IU pour iOS à la solution**

 Étendez cet exemple en ajoutant une IU native pour iOS. Pour tester le code sur iOS, vous devez vous connecter à un Mac sur votre réseau local, où sont installés Xcode et Xamarin. Une fois cette opération effectuée, vous pouvez utiliser le concepteur iOS directement dans Visual Studio. Consultez le [dépôt mobile-samples sur GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) pour obtenir une application complète.

 Consultez également la procédure pas à pas [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin).

 **Ajouter du code spécifique à une plateforme dans un projet partagé**

 Le code partagé dans une bibliothèque .NET Standard est indépendant de la plateforme. La bibliothèque est compilée une seule fois et incluse dans chaque package d’application spécifique à la plateforme. Si vous souhaitez écrire du code partagé qui utilise la compilation conditionnelle pour isoler le code spécifique à la plateforme, vous pouvez utiliser un projet *partagé*. Pour plus d’informations, consultez [Options de partage de code](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies).

## <a name="see-also"></a>Voir aussi

- [Documentation de Xamarin](http://docs.microsoft.com/xamarin)
- [Centre de développement Windows](https://dev.windows.com/en-us)
- [Affiche aide-mémoire pour Swift et C#](http://aka.ms/scposter)
