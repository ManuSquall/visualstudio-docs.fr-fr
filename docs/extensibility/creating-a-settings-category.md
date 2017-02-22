---
title: "Cr&#233;ation d’une cat&#233;gorie de param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres du profil, créer des catégories"
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 39
---
# Cr&#233;ation d’une cat&#233;gorie de param&#232;tres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans cette procédure pas à pas vous créez une catégorie de paramètres Visual Studio et l’utiliser pour enregistrer les valeurs et restaurer les valeurs à partir d’un fichier de paramètres. Une catégorie de paramètres est un groupe de propriétés connexes qui apparaissent sous la forme d’un « point de paramètres personnalisés ; » Autrement dit, en tant qu’une case à cocher dans le **importation et exportation de paramètres** Assistant. \(Vous pouvez le trouver sur le **outils** menu.\) Paramètres enregistrés ou restaurés comme une catégorie et les paramètres individuels ne sont pas affichés dans l’Assistant. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Vous créez une catégorie de paramètres en dérivant de la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.  
  
 Pour démarrer cette procédure pas à pas, vous devez effectuer la première section de [Création d’une Page d’Options](../extensibility/creating-an-options-page.md). La grille des propriétés qui en résulte Options vous permet d’examiner et modifier les propriétés de la catégorie. Après avoir enregistré la catégorie de propriété dans un fichier de paramètres, vous examinez le fichier pour voir comment les valeurs de propriété sont stockées.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’une catégorie de paramètres  
 Dans cette section, vous utilisez un point de paramètres personnalisés pour enregistrer et restaurer les valeurs de la catégorie de paramètres.  
  
#### Pour créer une catégorie de paramètres  
  
1.  Terminer la [Création d’une Page d’Options](../extensibility/creating-an-options-page.md).  
  
2.  Ouvrez le fichier VSPackage.resx et ajoutez ces ressources de chaîne de trois :  
  
    |Nom|Valeur|  
    |---------|------------|  
    |106|Ma catégorie|  
    |107|Mes paramètres|  
    |108|OptionInteger et OptionFloat|  
  
     Cela crée les ressources ce nom de la catégorie « My Category », l’objet « mes paramètres » et la description de la catégorie « OptionInteger et OptionFloat ».  
  
    > [!NOTE]
    >  Parmi ces trois, uniquement le nom de catégorie n’apparaît pas dans l’Assistant Importation et exportation de paramètres.  
  
3.  Dans MyToolsOptionsPackage.cs, ajoutez un `float` propriété nommée `OptionFloat` à la `OptionPageGrid` classe, comme indiqué dans l’exemple suivant.  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Le `OptionPageGrid` catégorie nommée « My Category » maintenant se compose des deux propriétés, `OptionInteger` et `OptionFloat`.  
  
4.  Ajouter un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> pour la `MyToolsOptionsPackage` classe et donnez\-lui le nom de la catégorie « My Category », attribuez\-lui ObjectName « Mes paramètres » et isToolsOptionPage la valeur true. Définissez les categoryResourceID, objectNameResourceID et DescriptionResourceID à la ressource correspondante de la chaîne Qu'id créés précédemment.  
  
    ```c#  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Générez le projet et commencez le débogage. Dans l’instance expérimentale, vous devez voir que **Ma Page de grille** a maintenant des valeurs integer et float.  
  
## Examen du fichier de paramètres  
 Dans cette section, vous exportez les valeurs de catégorie de propriété dans un fichier de paramètres. Vous examinez le fichier et puis réimportez les valeurs dans la catégorie de propriété.  
  
1.  Démarrer le projet en mode débogage en appuyant sur F5. Cela démarre l’instance expérimentale.  
  
2.  Ouvrez le **Outils \/ Options** boîte de dialogue.  
  
3.  Dans l’arborescence dans le volet gauche, développez **Mes catégorie** puis **Ma Page de grille**.  
  
4.  Modifiez la valeur de **OptionFloat** à 3.1416 et **OptionInteger** et 12. Cliquez sur **OK**.  
  
5.  Dans le menu **Outils**, cliquez sur **Importation et exportation des paramètres**.  
  
     Le **importation et exportation de paramètres** Assistant s’affiche.  
  
6.  Assurez\-vous que **Exporter les paramètres d’environnement sélectionnés** est sélectionnée, puis cliquez sur **Suivant**.  
  
     Le **Choisir les paramètres d’exportation** page s’affiche.  
  
7.  Cliquez sur **Mes paramètres**.  
  
     Le **Description** devient **OptionInteger et OptionFloat**.  
  
8.  Assurez\-vous que **Mes paramètres** est la seule catégorie qui est sélectionnée, puis cliquez sur **Suivant**.  
  
     Le **nom de votre fichier de paramètres** page s’affiche.  
  
9. Nommez le nouveau fichier de paramètres `MySettings.vssettings` et enregistrez\-le dans un répertoire approprié. Cliquez sur **Terminer**.  
  
     Le **exportation terminée** page signale que vos paramètres ont été exportés avec succès.  
  
10. Sur le **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**. Recherchez `MySettings.vssettings` et ouvrez\-le.  
  
     Vous trouverez la catégorie de propriété que vous avez exporté dans la section suivante du fichier \(vos GUID diffèrent\).  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     Notez que le nom complet de catégorie est formé par l’ajout d’un trait de soulignement le nom de catégorie suivi du nom de l’objet. OptionFloat et OptionInteger s’affichent dans la catégorie, ainsi que leurs valeurs exportés.  
  
11. Fermez le fichier de paramètres sans le modifier.  
  
12. Sur le **outils** menu, cliquez sur **Options**, développez **Mes catégories**, cliquez sur **Ma Page de grille** et modifiez la valeur de **OptionFloat** 1.0 et **OptionInteger** à 1. Cliquez sur **OK**.  
  
13. Sur le **outils** menu, cliquez sur **importation et exportation de paramètres**, sélectionnez **Importer les paramètres d’environnement sélectionnés**, puis cliquez sur **Suivant**.  
  
     Le **Enregistrer les paramètres actuels** page s’affiche.  
  
14. Sélectionnez **non, importer simplement de nouveaux paramètres** puis **Suivant**.  
  
     Le **Choisir une Collection de paramètres à importer** page s’affiche.  
  
15. Sélectionnez le `MySettings.vssettings` de fichiers dans le **Mes paramètres** nœud de l’arborescence. Si le fichier n’apparaît pas dans l’arborescence, cliquez sur **Parcourir** à trouver. Cliquez sur **Suivant**.  
  
     Le **Choisir les paramètres à importer** boîte de dialogue s’affiche.  
  
16. Assurez\-vous que **Mes paramètres** est sélectionnée, puis cliquez sur **Terminer**. Lors de la **importation complète** page s’affiche, cliquez sur **Fermer**.  
  
17. Sur le **outils** menu, cliquez sur **Options**, développez **Mes catégorie**, cliquez sur **Ma Page de grille** et vérifiez que les valeurs de catégorie de propriété ont été restaurés.