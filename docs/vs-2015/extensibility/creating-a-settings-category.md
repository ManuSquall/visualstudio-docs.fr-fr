---
title: Création d’une catégorie de paramètres | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60b500fa0defff3fc038ae4550f580dd7742939d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885607"
---
# <a name="creating-a-settings-category"></a>Création d’une catégorie de paramètres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez créer une catégorie de paramètres Visual Studio et l’utiliser pour enregistrer les valeurs et de restaurer les valeurs à partir d’un fichier de paramètres. Une catégorie de paramètres est un groupe de propriétés connexes qui apparaissent sous la forme d’un « point de paramètres personnalisés ; » Autrement dit, comme une case à cocher dans la **importation et exportation de paramètres** Assistant. (Vous pouvez le trouver sur le **outils** menu.) Les paramètres sont enregistrés ou restaurés en tant que catégorie, et les paramètres individuels ne sont pas affichés dans l’Assistant. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Vous créez une catégorie de paramètres en dérivant de la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.  
  
 Pour démarrer cette procédure pas à pas, vous devez tout d’abord effectuer la première section de [création d’une Page d’Options](../extensibility/creating-an-options-page.md). La grille des propriétés qui en résulte Options vous permet d’examiner et modifier les propriétés dans la catégorie. Après avoir enregistré la catégorie de propriété dans un fichier de paramètres, vous examinez le fichier pour voir comment les valeurs de propriété sont stockées.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Création d’une catégorie de paramètres  
 Dans cette section, vous utilisez un point de paramètres personnalisés pour enregistrer et restaurer les valeurs de la catégorie de paramètres.  
  
#### <a name="to-create-a-settings-category"></a>Pour créer une catégorie de paramètres  
  
1.  Terminer la [création d’une Page d’Options](../extensibility/creating-an-options-page.md).  
  
2.  Ouvrez le fichier VSPackage.resx et ajouter ces ressources de chaîne de trois :  
  
    |Name|Value|  
    |----------|-----------|  
    |106|Ma catégorie|  
    |107|Mes paramètres|  
    |108|OptionInteger et OptionFloat|  
  
     Cela crée les ressources ce nom de la catégorie « My Category », l’objet « mes paramètres » et la description de la catégorie « OptionInteger et OptionFloat ».  
  
    > [!NOTE]
    >  Parmi ces trois, uniquement le nom de catégorie n’apparaît pas dans l’Assistant Importation et exportation de paramètres.  
  
3.  Dans MyToolsOptionsPackage.cs, ajoutez un `float` propriété nommée `OptionFloat` à la `OptionPageGrid` classe, comme indiqué dans l’exemple suivant.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Le `OptionPageGrid` catégorie nommée « My Category » maintenant se compose des deux propriétés, `OptionInteger` et `OptionFloat`.  
  
4.  Ajouter un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> à la `MyToolsOptionsPackage` classe et donnez-lui le nom de la catégorie « My Category », attribuez-lui le NomObjet « Mes paramètres », puis isToolsOptionPage la valeur true. Définir categoryResourceID, objectNameResourceID et DescriptionResourceID à la ressource de chaîne correspondant Qu'id créés précédemment.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Générez le projet et commencez le débogage. Dans l’instance expérimentale, vous devez voir que **ma Page de grille** a maintenant des valeurs integer et float.  
  
## <a name="examining-the-settings-file"></a>Examen du fichier de paramètres  
 Dans cette section, vous exportez les valeurs de catégorie de propriété vers un fichier de paramètres. Vous examinez le fichier et réimportez les valeurs dans la catégorie de propriété.  
  
1.  Démarrez le projet en mode débogage en appuyant sur F5. Cela démarre l’instance expérimentale.  
  
2.  Ouvrez le **Outils / Options** boîte de dialogue.  
  
3.  Dans l’arborescence de commandes dans le volet gauche, développez **ma catégorie** puis cliquez sur **ma Page de grille**.  
  
4.  Modifiez la valeur de **OptionFloat** à 3.1416 et **OptionInteger** et 12. Cliquez sur **OK**.  
  
5.  Sur le **outils** menu, cliquez sur **importation et exportation de paramètres**.  
  
     Le **importation et exportation de paramètres** Assistant s’affiche.  
  
6.  Assurez-vous que **exporter les paramètres d’environnement sélectionnés** est sélectionnée, puis cliquez sur **suivant**.  
  
     Le **choisir les paramètres à exporter** page s’affiche.  
  
7.  Cliquez sur **mes paramètres**.  
  
     Le **Description** devient **OptionInteger et OptionFloat**.  
  
8.  Assurez-vous que l’option **mes paramètres** est la seule catégorie est sélectionnée, puis cliquez sur **suivant**.  
  
     Le **nom de votre fichier de paramètres** page s’affiche.  
  
9. Nommez le nouveau fichier de paramètres `MySettings.vssettings` et enregistrez-le dans un répertoire approprié. Cliquez sur **Terminer**.  
  
     Le **exportation terminée** page signale que vos paramètres ont été exportés avec succès.  
  
10. Sur le **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**. Recherchez `MySettings.vssettings` et ouvrez-le.  
  
     Vous trouverez la catégorie de propriété que vous avez exporté dans la section suivante du fichier (votre GUID varient).  
  
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
  
     Notez que le nom de catégorie complète est formé par l’ajout d’un trait de soulignement pour le nom de catégorie suivi du nom de l’objet. OptionFloat et OptionInteger apparaissent dans la catégorie, ainsi que leurs valeurs exportées.  
  
11. Fermez le fichier de paramètres sans le modifier.  
  
12. Sur le **outils** menu, cliquez sur **Options**, développez **ma catégorie**, cliquez sur **ma Page de grille** puis modifiez la valeur de  **OptionFloat** 1.0 et **OptionInteger** à 1. Cliquez sur **OK**.  
  
13. Sur le **outils** menu, cliquez sur **importation et exportation de paramètres**, sélectionnez **importer les paramètres d’environnement sélectionnés**, puis cliquez sur **suivant**.  
  
     Le **enregistrer les paramètres actuels** page s’affiche.  
  
14. Sélectionnez **non, importer simplement de nouveaux paramètres** puis cliquez sur **suivant**.  
  
     Le **choisir une Collection de paramètres à importer** page s’affiche.  
  
15. Sélectionnez le `MySettings.vssettings` de fichiers dans le **mes paramètres** nœud de l’arborescence. Si le fichier n’apparaît pas dans l’arborescence, cliquez sur **Parcourir** et de le retrouver. Cliquez sur **Suivant**.  
  
     Le **choisir les paramètres à importer** boîte de dialogue s’affiche.  
  
16. Assurez-vous que l’option **mes paramètres** est sélectionnée, puis cliquez sur **Terminer**. Lorsque le **importation complète** page s’affiche, cliquez sur **fermer**.  
  
17. Sur le **outils** menu, cliquez sur **Options**, développez **ma catégorie**, cliquez sur **ma Page de grille** et vérifiez que les valeurs de catégorie de propriété été restaurée.

