---
title: 'Comment : personnaliser un package de solution SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77b66160d489f711b5588fdcdd024d13769d734f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016868"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Comment : personnaliser un package de solution SharePoint
  Vous pouvez utiliser le concepteur de packages pour créer et personnaliser un package (*. wsp*). Par exemple, vous pouvez ajouter des fonctionnalités et des éléments de projet SharePoint, spécifier si le serveur Web est réinitialisé lorsque la solution est déployée et définir le type de serveur de déploiement.

## <a name="open-the-package-designer"></a>Ouvrir le concepteur de packages

#### <a name="to-open-the-package-designer"></a>Pour ouvrir le concepteur de packages

- Dans **Explorateur de solutions**, double-cliquez sur **package**, ou choisissez **Concepteur de vues** dans le menu contextuel du **package**.

## <a name="view-the-packaged-manifestffile"></a>Afficher les manifestfFile empaquetés
 Vous pouvez utiliser le concepteur de packages pour modifier et générer le fichier manifeste empaqueté. Ensuite, vous pouvez afficher le code XML de ce fichier dans Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>Pour afficher le fichier source XML

1. Dans le **Concepteur de packages**, choisissez **manifeste**.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Pour afficher le fichier manifeste empaqueté à l’aide de Explorateur de solutions

1. Dans l’**Explorateur de solutions**, choisissez **Afficher tous les fichiers**.

2. Développez package, développez package. Package, puis ouvrez le fichier *Package.Template.xml* .

    > [!NOTE]
    > Lorsque vous ouvrez le fichier manifeste XML pour le modèle de package, les fichiers sont validés automatiquement et vous pouvez ignorer les avertissements qui s’affichent dans la fenêtre de Liste d’erreurs.

## <a name="change-the-manifest-template"></a>Modifier le modèle de manifeste
 Vous pouvez modifier le code XML du fichier manifeste empaqueté dans l’éditeur XML de Visual Studio ou dans le volet modèle de manifeste. Toutes les modifications apportées au code XML sont fusionnées dans le fichier manifeste empaqueté pour le package.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Pour modifier le modèle de manifeste à l’aide de l’éditeur XML

1. Dans le **Concepteur de packages**, choisissez l’onglet **manifeste** , développez le nœud **options de modification** , puis cliquez sur le lien **ouvrir dans l’éditeur XML** .

     Les modifications apportées au code XML sont fusionnées dans le fichier manifeste empaqueté.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Pour modifier le modèle de manifeste à l’aide du volet modèle de manifeste

1. Dans le **Concepteur de packages**, choisissez l’onglet **manifeste** , développez le nœud **options de modification** , puis modifiez le XML qui s’affiche dans le volet modèle de manifeste.

     Les modifications apportées au XML s’affichent dans le volet **Aperçu du manifeste du package** .

## <a name="overwrite-the-packaged-manifest-file"></a>Remplacer le fichier manifeste empaqueté
 Vous pouvez désactiver le concepteur de packages et créer le fichier *manifest.xml* manuellement. La première fois que vous effectuez cette procédure, les paramètres actuels du concepteur de packages sont enregistrés dans le fichier XML du modèle de package. Ensuite, vous pouvez modifier ou remplacer le code XML.

> [!NOTE]
> Si vous ajoutez ou supprimez des éléments de projet SharePoint et des fonctionnalités dans le fichier XML alors que le concepteur de packages est désactivé, ces éléments et fonctionnalités de projet ne sont pas empaquetés.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Pour remplacer le fichier manifeste empaqueté en désactivant le concepteur

1. Dans le **Concepteur de packages**, choisissez l’onglet **manifeste** .

2. Développez le nœud **options de modification** , choisissez le lien remplacer le fichier **XML généré et modifier le manifeste dans l’éditeur XML** , puis choisissez le bouton **Oui** .

     Le modèle est mis à jour avec le fichier manifeste empaqueté actuel.

## <a name="enable-the-package-designer"></a>Activer le concepteur de packages
 Vous pouvez réactiver le concepteur de packages pour personnaliser le fichier *manifest.xml* .

#### <a name="to-re-enable-the-designer"></a>Pour réactiver le concepteur

1. Dans le **Concepteur de packages**, choisissez le lien **Ignorer les modifications du manifeste et réactiver le concepteur** , puis choisissez le bouton **Oui** .

     Le modèle est actualisé avec le texte d’origine et toute modification apportée au code XML est perdue.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
