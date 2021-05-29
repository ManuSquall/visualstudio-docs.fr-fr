---
title: Création d’une catégorie de paramètres | Microsoft Docs
description: Découvrez comment créer une catégorie de paramètres Visual Studio et l’utiliser pour enregistrer et restaurer des valeurs à partir d’un fichier de paramètres.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe46ea835a119978fd3decd26949db3d59944e5e
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687620"
---
# <a name="create-a-settings-category"></a>Créer une catégorie de paramètres

Dans cette procédure pas à pas, vous allez créer une catégorie de paramètres Visual Studio et l’utiliser pour enregistrer des valeurs dans un fichier de paramètres et les restaurer. Une catégorie de paramètres est un groupe de propriétés associées qui apparaissent sous la forme d’un « point de paramètres personnalisés ». autrement dit, il s’agit d’une case à cocher dans l’Assistant **importation et exportation de paramètres** . (Vous pouvez le trouver dans le menu **Outils** .) Les paramètres sont enregistrés ou restaurés en tant que catégorie, et les paramètres individuels ne sont pas affichés dans l’Assistant. Pour plus d’informations, consultez [Paramètres d’environnement](../ide/environment-settings.md).

Vous créez une catégorie de paramètres en la dérivant de la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.

Pour démarrer cette procédure pas à pas, vous devez d’abord terminer la première section de la [page créer une page d’options](../extensibility/creating-an-options-page.md). La grille des propriétés options qui en résulte vous permet d’examiner et de modifier les propriétés de la catégorie. Une fois que vous avez enregistré la catégorie de propriété dans un fichier de paramètres, vous examinez le fichier pour voir comment les valeurs de propriété sont stockées.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Créer une catégorie de paramètres
 Dans cette section, vous utilisez un point de paramètres personnalisés pour enregistrer et restaurer les valeurs de la catégorie de paramètres.

### <a name="to-create-a-settings-category"></a>Pour créer une catégorie de paramètres

1. Complétez la [page créer une option](../extensibility/creating-an-options-page.md).

2. Ouvrez le fichier *VSPackage. resx* et ajoutez ces trois ressources de type chaîne :

    |Name|Valeur|
    |----------|-----------|
    |106|Ma catégorie|
    |107|My Settings|
    |108|OptionInteger et OptionFloat|

     Cela crée des ressources qui dénomment la catégorie « ma catégorie », l’objet « mes paramètres » et la description de catégorie « OptionInteger et OptionFloat ».

    > [!NOTE]
    > Parmi ces trois, seul le nom de la catégorie n’apparaît pas dans l’Assistant **importation et exportation de paramètres** .

3. Dans *MyToolsOptionsPackage. cs*, ajoutez une `float` propriété nommée `OptionFloat` à la `OptionPageGrid` classe, comme indiqué dans l’exemple suivant.

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
    > La `OptionPageGrid` catégorie nommée « ma catégorie » comprend maintenant les deux propriétés, `OptionInteger` et `OptionFloat` .

4. Ajoutez un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> à la `MyToolsOptionsPackage` classe et donnez-lui le NomCatégorie « ma catégorie », donnez-lui la valeur ObjectName « mes paramètres », puis affectez à isToolsOptionPage la valeur true. Définissez categoryResourceID, objectNameResourceID et DescriptionResourceID sur les ID de ressource de chaîne correspondants créés précédemment.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Générez le projet et commencez le débogage. Dans l’instance expérimentale, vous devez voir que la page de la **grille** contient à présent des valeurs entières et flottantes.

## <a name="examine-the-settings-file"></a>Examiner le fichier de paramètres
 Dans cette section, vous exportez des valeurs de catégorie de propriété dans un fichier de paramètres. Vous examinez le fichier, puis réimportez les valeurs dans la catégorie de propriété.

1. Démarrez le projet en mode débogage en appuyant sur **F5**. Cela démarre l’instance expérimentale.

2. Ouvrez la   >  boîte de dialogue **options** des outils.

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

9. Nommez le nouveau fichier de paramètres *MySettings. vssettings* , puis enregistrez-le dans un répertoire approprié. Cliquez sur **Terminer**.

   Le `.vssettings` fichier est le fichier de paramètres de Visual Studio. Le schéma du fichier est ouvert. Le plus souvent, le schéma suit une structure XML où chaque catégorie est une balise, qui peut elle-même contenir des balises de sous-catégorie. Ces balises de sous-catégorie peuvent contenir des balises de valeur de propriété. Alors que la plupart des packages utilisent la structure commune, tout package dans Visual Studio peut apporter des données XML arbitraires au fichier avec le schéma qu’il choisit.

   La page **exportation terminée** signale que vos paramètres ont été exportés avec succès.

10. Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier**. Recherchez *MySettings. vssettings* et ouvrez-le.

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

15. Sélectionnez le fichier *MySettings. vssettings* dans le nœud **mes paramètres** de l’arborescence. Si le fichier n’apparaît pas dans l’arborescence, cliquez sur **Parcourir** et recherchez-le. Cliquez sur **Suivant**.

     La boîte de dialogue **choisir les paramètres à importer** s’affiche.

16. Assurez-vous que **mes paramètres** est sélectionné, puis cliquez sur **Terminer**. Lorsque la page **importation terminée** s’affiche, cliquez sur **Fermer**.

17. Dans le menu **Outils** , cliquez sur **options**, développez **ma catégorie**, cliquez sur **ma page de grille** et vérifiez que les valeurs de catégorie de propriété ont été restaurées.
