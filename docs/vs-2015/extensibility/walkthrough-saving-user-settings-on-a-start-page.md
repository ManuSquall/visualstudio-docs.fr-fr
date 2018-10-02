---
title: 'Procédure pas à pas : Enregistrement des paramètres utilisateur sur une Page de démarrage | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 213f09b4cef1a3530e4759caf5700630fe3319d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496366"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Procédure pas à pas : enregistrement des paramètres utilisateur sur une page de démarrage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : enregistrement des paramètres utilisateur sur une Page de démarrage](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-saving-user-settings-on-a-start-page).  
  
Vous pouvez conserver les paramètres utilisateur de votre page de démarrage. En suivant cette procédure pas à pas, vous pouvez créer un contrôle qui enregistre un paramètre dans le Registre lorsque l’utilisateur clique sur un bouton et récupère ensuite que la définition de chaque chargement de la Page de démarrage. Étant donné que le modèle de projet Page de démarrage inclut un contrôle utilisateur personnalisable, et le XAML de Page de démarrage par défaut appelle ce contrôle, il est inutile de modifier la Page de démarrage lui-même.  
  
 La banque de paramètres est instanciée dans cette procédure pas à pas est une instance de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interface, qui lit et écrit dans l’emplacement de Registre suivant lorsqu’elle est appelée : HKCU\Software\Microsoft\VisualStudio\14.0\\  *CollectionName*  
  
 Lorsqu’il s’exécute dans l’instance expérimentale de Visual Studio, la banque de paramètres lit et écrit dans HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName.*  
  
 Pour plus d’informations sur la façon de conserver les paramètres, consultez [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Prérequis  
  
> [!NOTE]
>  Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  Vous pouvez télécharger le modèle de projet Page de démarrage à l’aide de **Gestionnaire d’extensions**.  
  
## <a name="setting-up-the-project"></a>Configuration du projet  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Pour configurer le projet pour cette procédure pas à pas  
  
1.  Créez un projet de Page de démarrage en utilisant le modèle de projet Page de démarrage, comme décrit dans [création d’un votre Page de démarrage propre](../misc/creating-your-own-start-page.md). Nommez le projet **SaveMySettings**.  
  
2.  Dans **l’Explorateur de solutions**, ajoutez les références d’assembly suivantes au projet StartPageControl :  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Assemblys Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Ouvrez MyControl.xaml.  
  
4.  Dans le volet XAML, dans le niveau supérieur <xref:System.Windows.Controls.UserControl> définition de l’élément, ajoutez la déclaration d’événement suivante après les déclarations d’espace de noms.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  Dans le volet de conception, cliquez sur la zone principale du contrôle et appuyez sur SUPPR.  
  
     Cette opération supprime le <xref:System.Windows.Controls.Border> élément et tous les éléments et laisse uniquement le niveau supérieur <xref:System.Windows.Controls.Grid> élément.  
  
6.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Controls.StackPanel> contrôle à la grille.  
  
7.  Maintenant, faites glisser un <xref:System.Windows.Controls.TextBlock>, un <xref:System.Windows.Controls.TextBox>et un bouton pour le <xref:System.Windows.Controls.StackPanel>.  
  
8.  Ajouter un **x : Name** d’attribut pour le <xref:System.Windows.Controls.TextBox>et un `Click` événement pour le <xref:System.Windows.Controls.Button>, comme illustré dans l’exemple suivant.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implémentation du contrôle utilisateur  
  
#### <a name="to-implement-the-user-control"></a>Pour implémenter le contrôle utilisateur  
  
1.  Dans le volet XAML, cliquez sur le `Click` attribut de la <xref:System.Windows.Controls.Button> élément, puis cliquez sur **naviguez jusqu’au gestionnaire d’événements**.  
  
     Cela ouvre MyControl.xaml.cs et crée un gestionnaire de stub pour la `Button_Click` événement.  
  
2.  Ajoutez le code suivant `using` instructions au début du fichier.  
  
     [!code-csharp[StartPageDTE#11](../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs#11)]  
  
3.  Ajouter une privée `SettingsStore` propriété, comme indiqué dans l’exemple suivant.  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     Cette propriété obtient d’abord une référence à la <xref:EnvDTE80.DTE2> interface, qui contient le modèle objet Automation, à partir de la <xref:System.Windows.FrameworkElement.DataContext%2A> du contrôle utilisateur, puis utilise l’objet DTE pour obtenir une instance de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interface. Il utilise ensuite cette instance pour retourner les paramètres utilisateur actuels.  
  
4.  Renseignez le `Button_Click` événements comme suit.  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     Il écrit le contenu de la zone de texte dans un champ « MySetting » dans une collection de « MySettings » dans le Registre. Si la collection n’existe pas, il est créé.  
  
5.  Ajoutez le gestionnaire suivant pour le `OnLoaded` événement du contrôle utilisateur.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Cela définit le texte de la zone de texte sur la valeur actuelle de « MySetting ».  
  
6.  Générer le contrôle utilisateur.  
  
7.  Dans **l’Explorateur de solutions**, ouvrez source.extension.vsixmanifest.  
  
8.  Dans l’éditeur de manifeste, définissez **Product Name** à **enregistrer la Page de démarrage des paramètres de mes**.  
  
     Cela définit le nom de la Page de démarrage, tel qu’il doit apparaître dans le **personnaliser la Page de démarrage** liste dans le **Options** boîte de dialogue.  
  
9. Build StartPage.xaml.  
  
## <a name="testing-the-control"></a>Test du contrôle  
  
#### <a name="to-test-the-user-control"></a>Pour tester le contrôle utilisateur  
  
1.  Appuyez sur F5.  
  
     L’instance expérimentale de Visual Studio s’ouvre.  
  
2.  Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **Options**.  
  
3.  Dans le **environnement** nœud, cliquez sur **démarrage**, puis, dans le **personnaliser la Page de démarrage** liste, sélectionnez **[Extension installée] enregistrer mes paramètres de Page de démarrage** .  
  
     Cliquez sur **OK**.  
  
4.  Fermez la Page de démarrage s’il est ouvert, puis, dans le **vue** menu, cliquez sur **Page de démarrage**.  
  
5.  Dans la Page de démarrage, cliquez sur le **MyControl** onglet.  
  
6.  Dans la zone de texte, tapez **Cat**, puis cliquez sur **enregistrer mes paramètres**.  
  
7.  Fermez la Page de démarrage et ouvrez de nouveau.  
  
     Le mot « Cat » doit être affiché dans la zone de texte.  
  
8.  Remplacez le mot « Cat » par le mot « Dog ». Ne cliquez pas sur le bouton.  
  
9. Fermez la Page de démarrage et ouvrez de nouveau.  
  
     Le mot « Dog » doit être affiché dans la zone de texte, même si le paramètre n’a pas été enregistré. Cela se produit car Visual Studio conserve les fenêtres Outil dans la mémoire, même s’ils sont fermés, jusqu'à ce que Visual Studio lui-même est fermé.  
  
10. Fermez l’instance expérimentale de Visual Studio.  
  
11. Appuyez sur F5 pour ouvrir l’instance expérimentale.  
  
12. Le mot « Cat » doit être affiché dans la zone de texte.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous pouvez modifier ce contrôle utilisateur pour enregistrer et récupérer un nombre quelconque de paramètres personnalisés à l’aide des valeurs différentes à partir des gestionnaires d’événements différents pour obtenir et définir le `SettingsStore` propriété. Tant que vous utilisez un autre `propertyName` paramètre pour chaque appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, les valeurs ne remplacera pas l’autre dans le Registre.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>   
 [Création de votre propre Page de démarrage](../misc/creating-your-own-start-page.md)   
 [Ajout de commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)

