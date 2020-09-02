---
title: Création d’une catégorie de paramètres | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d14e60ec28fb5f8ba80f9986c4316058539b35e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695023"
---
# <a name="creating-a-settings-category"></a>Création d’une catégorie de paramètres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez créer une catégorie de paramètres Visual Studio et l’utiliser pour enregistrer des valeurs dans un fichier de paramètres et les restaurer. Une catégorie de paramètres est un groupe de propriétés associées qui apparaissent sous la forme d’un « point de paramètres personnalisés ». autrement dit, il s’agit d’une case à cocher dans l’Assistant **importation et exportation de paramètres** . (Vous pouvez le trouver dans le menu **Outils** .) Les paramètres sont enregistrés ou restaurés en tant que catégorie, et les paramètres individuels ne sont pas affichés dans l’Assistant. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Vous créez une catégorie de paramètres en la dérivant de la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.  
  
 Pour démarrer cette procédure pas à pas, vous devez d’abord terminer la première section de [création d’une page d’options](../extensibility/creating-an-options-page.md). La grille des propriétés options qui en résulte vous permet d’examiner et de modifier les propriétés de la catégorie. Une fois que vous avez enregistré la catégorie de propriété dans un fichier de paramètres, vous examinez le fichier pour voir comment les valeurs de propriété sont stockées.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Création d’une catégorie de paramètres  
 Dans cette section, vous utilisez un point de paramètres personnalisés pour enregistrer et restaurer les valeurs de la catégorie de paramètres.  
  
#### <a name="to-create-a-settings-category"></a>Pour créer une catégorie de paramètres  
  
1. Complétez la [page création d’une option](../extensibility/creating-an-options-page.md).  
  
2. Ouvrez le fichier VSPackage. resx et ajoutez ces trois ressources de type chaîne :  
  
    |Nom|Valeur|  
    |----------|-----------|  
    |106|Ma catégorie|  
    |107|My Settings|  
    |108|OptionInteger et OptionFloat|  
  
     Cela crée des ressources qui dénomment la catégorie « ma catégorie », l’objet « mes paramètres » et la description de catégorie « OptionInteger et OptionFloat ».  
  
    > [!NOTE]
    > Parmi ces trois, seul le nom de la catégorie n’apparaît pas dans l’Assistant importation et exportation de paramètres.  
  
3. Dans MyToolsOptionsPackage.cs, ajoutez une `float` propriété nommée `OptionFloat` à la `OptionPageGrid` classe, comme indiqué dans l’exemple suivant.  
  
    ```csharp  
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
    > La `OptionPageGrid` catégorie nommée « ma catégorie » comprend maintenant les deux propriétés, `OptionInteger` et `OptionFloat` .  
  
4. Ajoutez un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> à la `MyToolsOptionsPackage` classe et donnez-lui le NomCatégorie « ma catégorie », donnez-lui la valeur ObjectName « mes paramètres », puis affectez à isToolsOptionPage la valeur true. Définissez categoryResourceID, objectNameResourceID et DescriptionResourceID sur les ID de ressource de chaîne correspondants créés précédemment.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5. Générez le projet et commencez le débogage. Dans l’instance expérimentale, vous devez voir que la page de la **grille** contient à présent des valeurs entières et flottantes.  
  
## <a name="examining-the-settings-file"></a>Examen du fichier de paramètres  
 Dans cette section, vous exportez des valeurs de catégorie de propriété dans un fichier de paramètres. Vous examinez le fichier, puis réimportez les valeurs dans la catégorie de propriété.  
  
1. Démarrez le projet en mode débogage en appuyant sur F5. Cela démarre l’instance expérimentale.  
  
2. Ouvrez la boîte de dialogue **Outils/Options** .  
  
3. Dans l’arborescence dans le volet gauche, développez **ma catégorie** , puis cliquez sur **ma page de grille**.  
  
4. Remplacez la valeur de **OptionFloat** par 3,1416 et **OptionInteger** par 12. Cliquez sur **OK**.  
  
5. Dans le menu **Outils**, cliquez sur **Importation et exportation des paramètres**.  
  
     L’Assistant **importation et exportation de paramètres** s’affiche.  
  
6. Vérifiez que l’option **Exporter les paramètres d’environnement sélectionnés** est sélectionnée, puis cliquez sur **suivant**.  
  
     La page **choisir les paramètres à exporter** s’affiche.  
  
7. Cliquez sur **mes paramètres**.  
  
     La **Description** devient **OptionInteger et OptionFloat**.  
  
8. Assurez-vous que **mes paramètres** est la seule catégorie sélectionnée, puis cliquez sur **suivant**.  
  
     La page **nom de votre fichier de paramètres** s’affiche.  
  
9. Nommez le nouveau fichier de paramètres `MySettings.vssettings` et enregistrez-le dans un répertoire approprié. Cliquez sur **Terminer**.  
  
     La page **exportation terminée** signale que vos paramètres ont été exportés avec succès.  
  
10. Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier**. Localisez `MySettings.vssettings` et ouvrez-le.  
  
     Vous pouvez rechercher la catégorie de propriété que vous avez exportée dans la section suivante du fichier (vos GUID seront différents).  
  
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
  
     Notez que le nom complet de la catégorie est formé par l’ajout d’un trait de soulignement au nom de la catégorie, suivi du nom de l’objet. OptionFloat et OptionInteger s’affichent dans la catégorie, avec leurs valeurs exportées.  
  
11. Fermez le fichier de paramètres sans le modifier.  
  
12. Dans le menu **Outils** , cliquez **sur options**, développez **ma catégorie**, cliquez sur la **page mon grille** , puis remplacez la valeur de **OptionFloat** par la valeur 1,0 et **OptionInteger** par la valeur 1. Cliquez sur **OK**.  
  
13. Dans le menu **Outils** , cliquez sur **importation et exportation de paramètres**, sélectionnez Importer les paramètres d' **environnement sélectionnés**, puis cliquez sur **suivant**.  
  
     La page **enregistrer les paramètres actuels** s’affiche.  
  
14. Sélectionnez **non, importer simplement de nouveaux paramètres** , puis cliquez sur **suivant**.  
  
     La page **choisir une collection de paramètres à importer** s’affiche.  
  
15. Sélectionnez le `MySettings.vssettings` fichier dans le nœud **mes paramètres** de l’arborescence. Si le fichier n’apparaît pas dans l’arborescence, cliquez sur **Parcourir** et recherchez-le. Cliquez sur **Suivant**.  
  
     La boîte de dialogue **choisir les paramètres à importer** s’affiche.  
  
16. Assurez-vous que **mes paramètres** est sélectionné, puis cliquez sur **Terminer**. Lorsque la page **importation terminée** s’affiche, cliquez sur **Fermer**.  
  
17. Dans le menu **Outils** , cliquez sur **options**, développez **ma catégorie**, cliquez sur **ma page de grille** et vérifiez que les valeurs de catégorie de propriété ont été restaurées.
