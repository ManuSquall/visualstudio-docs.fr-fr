---
title: Mettre à jour de zones de formulaire dans les projets Outlook que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 84005dfa85c637d2ff5677e6ad02b811bd0cb671
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842802"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Mettre à jour de zones de formulaire dans les projets Outlook que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5
  Si l’infrastructure cible d’un projet de complément VSTO Outlook avec une zone de formulaire passe à [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez apporter quelques changements au code de zone de formulaire généré, ainsi qu’au code qui instancie certaines classes de zone de formulaire au moment de l’exécution.  
  
## <a name="update-the-generated-form-region-code"></a>Mettre à jour le code de région de formulaire généré  
 Si la version cible de .NET Framework du projet est remplacée par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez changer le code de zone de formulaire généré. Les changements que vous apportez ne sont pas les mêmes pour les zones de formulaire que vous avez créées dans Visual Studio, et les zones de formulaire que vous avez importées à partir d'Outlook. Pour plus d’informations sur les différences entre ces types de zones de formulaire, consultez [zones de formulaire Outlook créer](../vsto/creating-outlook-form-regions.md).  
  
### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Pour mettre à jour le code généré d'une zone de formulaire que vous avez créée dans Visual Studio  
  
1.  Ouvrez le fichier code-behind de zone de formulaire dans l'éditeur de code. Ce fichier se nomme *VotreZoneDeFormulaire*.Designer.cs ou *VotreZoneDeFormulaire*.Designer.vb. Pour afficher ce fichier dans les projets Visual Basic, cliquez sur le bouton **Afficher tous les fichiers** dans l' **Explorateur de solutions**.  
  
2.  Modifiez la déclaration de la classe de zone de formulaire pour qu'elle dérive de <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> au lieu de `Microsoft.Office.Tools.Outlook.FormRegionControl`.  
  
3.  Modifiez le constructeur de la classe de zone de formulaire, comme indiqué dans les exemples de code suivants.  
  
     L'exemple de code suivant montre le constructeur d'une classe de zone de formulaire dans un projet qui cible .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
     L'exemple de code suivant montre le constructeur d'une classe de zone de formulaire dans un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
4.  Modifiez la signature de la méthode `InitializeManifest` , comme indiqué ci-dessous. Assurez-vous de ne pas modifier le code de la méthode. Ce code représente les paramètres de zone de formulaire que vous avez appliqués dans le concepteur. Dans les projets Visual C#, vous devez développer la zone nommée `Form Region Designer generated code` pour voir cette méthode.  
  
     L'exemple de code suivant montre la signature de la méthode `InitializeManifest` dans un projet qui cible .NET Framework 3.5.  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
     L'exemple de code suivant montre la signature de la méthode `InitializeManifest` dans un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,   
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,   
        Microsoft.Office.Tools.Outlook.Factory factory)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
5.  Ajoutez un nouvel élément de zone de formulaire Outlook à votre projet. Ouvrez le fichier code-behind de la nouvelle zone de formulaire, recherchez les classes *VotreNouvelleZoneDeFormulaire*`Factory` et `WindowFormRegionCollection` dans le fichier, puis copiez ces classes vers le Presse-papiers.  
  
6.  Supprimez la nouvelle zone de formulaire que vous avez ajoutée à votre projet.  
  
7.  Dans le fichier code-behind de la zone de formulaire que vous mettez à jour pour qu'elle fonctionne dans le projet reciblé, localisez les classes *VotreZoneDeFormulaireInitiale*`Factory` et `WindowFormRegionCollection` , puis remplacez-les par le code que vous avez copié à partir de la nouvelle zone de formulaire.  
  
8.  Dans les classes *VotreNouvelleZoneDeFormulaire*`Factory` et `WindowFormRegionCollection` , recherchez toutes les références à la classe *VotreNouvelleZoneDeFormulaire* , puis remplacez chaque référence par la classe *VotreZoneDeFormulaireInitiale* . Par exemple, si la zone de formulaire que vous mettez à jour se nomme `SalesDataFormRegion` , et si la zone de formulaire que vous avez créée à l'étape 5 se nomme `FormRegion1`, remplacez toutes les références de `FormRegion1` par `SalesDataFormRegion`.  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Pour mettre à jour le code généré d'une zone de formulaire que vous avez importée à partir d'Outlook  
  
1.  Ouvrez le fichier code-behind de zone de formulaire dans l'éditeur de code. Ce fichier se nomme *VotreZoneDeFormulaire*.Designer.cs ou *VotreZoneDeFormulaire*.Designer.vb. Pour afficher ce fichier dans les projets Visual Basic, cliquez sur le bouton **Afficher tous les fichiers** dans l' **Explorateur de solutions**.  
  
2.  Modifiez la déclaration de la classe de zone de formulaire pour qu'elle dérive de <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> au lieu de `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.  
  
3.  Modifiez le constructeur de la classe de zone de formulaire, comme indiqué dans les exemples de code suivants.  
  
     L'exemple de code suivant montre le constructeur d'une classe de zone de formulaire dans un projet qui cible .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
     L'exemple de code suivant montre la signature du constructeur d'une classe de zone de formulaire dans un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
4.  Pour chaque ligne de code de la méthode `InitializeControls` qui initialise un contrôle dans la classe de zone de formulaire, modifiez le code comme indiqué ci-dessous.  
  
     L'exemple de code suivant montre comment initialiser un contrôle dans un projet qui cible .NET Framework 3.5. Dans ce code, la méthode `GetFormRegionControl` possède un paramètre de type qui spécifie le type du contrôle retourné.  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     L'exemple de code suivant montre comment initialiser un contrôle dans un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Dans ce code, la méthode <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> n'a aucun paramètre de type. Vous devez caster la valeur de retour vers le type du contrôle que vous initialisez.  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  Ajoutez un nouvel élément de zone de formulaire Outlook à votre projet. Ouvrez le fichier code-behind de la nouvelle zone de formulaire, recherchez les classes *VotreNouvelleZoneDeFormulaire*`Factory` et `WindowFormRegionCollection` dans le fichier, puis copiez ces classes vers le Presse-papiers.  
  
6.  Supprimez la nouvelle zone de formulaire que vous avez ajoutée à votre projet.  
  
7.  Dans le fichier code-behind de la zone de formulaire que vous mettez à jour pour qu'elle fonctionne dans le projet reciblé, localisez les classes *VotreZoneDeFormulaireInitiale*`Factory` et `WindowFormRegionCollection` , puis remplacez-les par le code que vous avez copié à partir de la nouvelle zone de formulaire.  
  
8.  Dans les classes *VotreNouvelleZoneDeFormulaire*`Factory` et `WindowFormRegionCollection` , recherchez toutes les références à la classe *VotreNouvelleZoneDeFormulaire* , puis remplacez chaque référence par la classe *VotreZoneDeFormulaireInitiale* . Par exemple, si la zone de formulaire que vous mettez à jour se nomme `SalesDataFormRegion` , et si la zone de formulaire que vous avez créée à l'étape 5 se nomme `FormRegion1`, remplacez toutes les références de `FormRegion1` par `SalesDataFormRegion`.  
  
## <a name="instantiate-form-region-classes"></a>Instancier des classes de zone de formulaire  
 Vous devez modifier tout code qui instancie dynamiquement certaines classes de zone de formulaire. Dans les projets qui ciblent .NET Framework 3.5, vous pouvez instancier directement des classes de zone de formulaire telles que `Microsoft.Office.Tools.Outlook.FormRegionManifest`. Dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, ces classes sont des interfaces que vous ne pouvez pas instancier directement.  
  
 Si la version cible de .NET Framework du projet est remplacée par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez instancier les interfaces à l'aide des méthodes fournies par la propriété `Globals.Factory`. Pour plus d’informations sur la `Globals.Factory` propriété, consultez [d’accès Global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Le tableau suivant répertorie les types de zone de formulaire et la méthode à utiliser pour instancier les types dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure.  
  
|Type|Méthode de fabrique à utiliser|  
|----------|---------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## <a name="see-also"></a>Voir aussi  
 [Migrer des solutions Office vers .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)  
