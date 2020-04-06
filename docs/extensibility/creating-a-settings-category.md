---
title: Création d’une catégorie Paramètres (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739607"
---
# <a name="create-a-settings-category"></a>Créer une catégorie de paramètres

Dans cette procédure pas à pas, vous créez une catégorie de paramètres Visual Studio et l’utilisez pour enregistrer des valeurs et restaurer les valeurs d’un fichier de paramètres. Une catégorie de paramètres est un groupe de propriétés connexes qui apparaissent comme un « point de réglage personnalisé »; c’est-à-dire comme une case à cocher dans **l’assistant Des paramètres d’importation et d’exportation.** (Vous pouvez le trouver sur le menu **Tools.)** Les paramètres sont enregistrés ou restaurés en tant que catégorie, et les paramètres individuels ne sont pas affichés dans l’assistant. Pour plus d’informations, consultez [Paramètres d’environnement](../ide/environment-settings.md).

Vous créez une catégorie de paramètres <xref:Microsoft.VisualStudio.Shell.DialogPage> en la récupérant de la classe.

Pour commencer cette procédure pas à pas, vous devez d’abord compléter la première section de [Créer une page Options](../extensibility/creating-an-options-page.md). Le réseau de propriété Options qui en résulte vous permet d’examiner et de modifier les propriétés de la catégorie. Après avoir enregistré la catégorie de propriété dans un fichier de paramètres, vous examinez le fichier pour voir comment les valeurs de propriété sont stockées.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Créer une catégorie de paramètres
 Dans cette section, vous utilisez un point de réglage personnalisé pour enregistrer et restaurer les valeurs de la catégorie paramètres.

### <a name="to-create-a-settings-category"></a>Créer une catégorie de paramètres

1. Complétez la [page Créer une option](../extensibility/creating-an-options-page.md).

2. Ouvrez le fichier *VSPackage.resx* et ajoutez ces trois ressources de cordes :

    |Nom|Valeur|
    |----------|-----------|
    |106|Ma catégorie|
    |107|My Settings|
    |108|OptionInteger et OptionFloat|

     Cela crée des ressources qui nomment la catégorie "Ma catégorie", l’objet "Mes Paramètres", et la description de catégorie "OptionInteger et OptionFloat".

    > [!NOTE]
    > De ces trois, seul le nom de la catégorie n’apparaît pas dans **l’assistant Des paramètres d’importation et d’exportation.**

3. Dans *MyToolsOptionsPackage.cs*, ajouter `float` une `OptionFloat` propriété `OptionPageGrid` nommée à la classe, comme indiqué dans l’exemple suivant.

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
    > La `OptionPageGrid` catégorie nommée "Ma catégorie" se `OptionInteger` compose `OptionFloat`maintenant des deux propriétés, et .

4. Ajoutez <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> un `MyToolsOptionsPackage` à la classe et lui donner le CategoryName "My Category", lui donner l’ObjectName "Mes Paramètres", et l’ensemble isToolsOptionPage à vrai. Définissez la catégorieResourceID, objectNameResourceID et DescriptionResourceID aux IDE de ressources de chaîne correspondantes créées précédemment.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Générez le projet et commencez le débogage. Dans le cas expérimental, vous devriez voir que **My Grid Page** a maintenant à la fois des valeurs d’intégrage et de flotteur.

## <a name="examine-the-settings-file"></a>Examiner le fichier paramètres
 Dans cette section, vous exportez des valeurs de catégorie de propriétés vers un fichier de paramètres. Vous examinez le fichier et importez ensuite les valeurs dans la catégorie des biens.

1. Démarrer le projet en mode débogé en appuyant sur **F5**. Cela commence l’instance expérimentale.

2. Ouvrez le dialogue **Tools** > **Options.**

3. Dans la vue de l’arbre dans la vitre gauche, étendre **ma catégorie,** puis cliquez sur **Ma page de grille**.

4. Changez la valeur **d’OptionFloat** à 3.1416 et **OptionInteger** à 12. Cliquez sur **OK**.

5. Dans le menu **Outils**, cliquez sur **Importation et exportation des paramètres**.

     **L’assistant Des paramètres d’importation et d’exportation** apparaît.

6. Assurez-vous que **les paramètres de l’environnement sélectionnés à l’exportation** sont sélectionnés, puis cliquez sur **Next**.

     La page **Paramètres de choix à l’exportation** apparaît.

7. Cliquez **sur Mes Paramètres**.

     La **description** change à **OptionInteger et OptionFloat**.

8. Assurez-vous que **Mes Paramètres** sont la seule catégorie qui est sélectionnée, puis cliquez sur **Next**.

     Le nom de votre page **de fichiers Paramètres** apparaît.

9. Nommez les nouveaux paramètres fichier *MySettings.vssettings* et enregistrez-le dans un répertoire approprié. Cliquez sur **Terminer**.

     La page **Export Complete** indique que vos paramètres ont été exportés avec succès.

10. Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier**. Localiser *MySettings.vssettings* et l’ouvrir.

     Vous pouvez trouver la catégorie de propriété que vous avez exportée dans la section suivante du fichier (vos GUIDs seront différents).

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

     Notez que le nom de la catégorie complète est formé par l’ajout d’un soulignement au nom de catégorie suivi du nom de l’objet. OptionFloat et OptionInteger apparaissent dans la catégorie, ainsi que leurs valeurs exportées.

11. Fermez le fichier des paramètres sans le modifier.

12. Sur le menu **Tools,** cliquez sur **Options**, étendre **ma catégorie**, cliquez sur My **Grid Page,** puis changez la valeur d’OptionFloat à 1.0 et **OptionFloat** **OptionInteger** à 1. Cliquez sur **OK**.

13. Sur le menu **Tools,** cliquez sur **Paramètres d’importation et d’exportation**, **sélectionnez Les paramètres de l’environnement sélectionnés Import,** puis cliquez sur **Next**.

     La page **Paramètres d’enregistrement actuel** apparaît.

14. Sélectionnez **Non, il suffit d’importer de nouveaux paramètres,** puis cliquez sur **Next**.

     La **page Choisir une collection de paramètres à importer** apparaît.

15. Sélectionnez le fichier *MySettings.vssettings* dans le nœud **My Settings** de la vue de l’arbre. Si le fichier n’apparaît pas dans la vue de l’arbre, cliquez sur **Parcourir** et le trouver. Cliquez sur **Suivant**.

     La boîte de dialogue **Choisir les paramètres d’importation** apparaît.

16. Assurez-vous que **Mes Paramètres** sont sélectionnés, puis cliquez sur **Finition**. Lorsque la page **Import Complete** s’affiche, cliquez sur **Close**.

17. Sur le menu **Tools,** cliquez sur **Options**, élargissez **ma catégorie**, cliquez sur My **Grid Page** et vérifiez que les valeurs de la catégorie de propriété ont été restaurées.
