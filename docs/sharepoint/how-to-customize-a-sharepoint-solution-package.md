---
title: 'Procédure : Personnaliser un Package de Solution SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 567eba3da4856cd88a583bf614d5afbc13e77b0d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074919"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Procédure : Personnaliser un package de solution SharePoint
  Vous pouvez utiliser le Concepteur de packages pour créer et personnaliser un package (*.wsp*). Par exemple, vous pouvez ajouter des éléments de projet SharePoint et des fonctionnalités, spécifiez si le serveur Web est réinitialisé lorsque la solution est déployée, définissez le type de serveur de déploiement.

## <a name="open-the-package-designer"></a>Ouvrez le Concepteur de packages

#### <a name="to-open-the-package-designer"></a>Pour ouvrir le Concepteur de packages

- Dans **l’Explorateur de solutions**, double-cliquez sur **Package**, ou choisissez **Concepteur de vue** dans le menu contextuel pour **Package**.

## <a name="view-the-packaged-manifestffile"></a>Afficher le manifestfFile empaquetée
 Vous pouvez utiliser le Concepteur de packages pour modifier et générer le fichier manifeste de package. Ensuite, vous pouvez afficher le code XML de ce fichier dans Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>Pour afficher le fichier de source XML

1. Dans le **Concepteur de packages**, choisissez **manifeste**.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Pour afficher le fichier manifeste de package à l’aide de l’Explorateur de solutions

1. Dans l’**Explorateur de solutions**, choisissez **Afficher tous les fichiers**.

2. Développez le Package, développez le package et ouvrez le *Package.Template.xml* fichier.

    > [!NOTE]
    >  Lorsque vous ouvrez le fichier XML de manifeste pour le modèle de package, les fichiers sont validés automatiquement, et vous pouvez ignorer les avertissements qui apparaissent dans la fenêtre liste d’erreurs.

## <a name="change-the-manifest-template"></a>Modifier le modèle de manifeste
 Vous pouvez modifier le code XML du fichier manifest du package dans l’éditeur XML de Visual Studio ou dans le volet modèle de manifeste. Toutes les modifications au code XML sont fusionnées dans le fichier manifest de package pour le package.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Pour modifier le modèle de manifeste à l’aide de l’éditeur XML

1. Dans le **Concepteur de packages**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud, puis choisissez le **ouvert dans l’éditeur XML** lien.

     Modifications apportées au document XML sont fusionnées dans le fichier manifest de package.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Pour modifier le modèle de manifeste en utilisant le volet modèle de manifeste

1. Dans le **Concepteur de packages**, choisissez le **manifeste** onglet, développez le **modifier les Options** nœud et modifiez le code XML qui s’affiche dans le volet modèle de manifeste.

     Modifications apportées au document XML s’affichent dans le **aperçu du manifeste ajouté au package** volet.

## <a name="overwrite-the-packaged-manifest-file"></a>Remplacer le fichier manifeste de package
 Vous pouvez désactiver le Concepteur de packages et créer le *manifest.xml* fichier manuellement. La première fois que vous procédez ainsi, les paramètres actuels dans le Concepteur de packages sont enregistrés au fichier XML de modèle de package. Ensuite, vous pouvez modifier ou remplacer le code XML.

> [!NOTE]
>  Si vous ajoutez ou supprimez des éléments de projet SharePoint et des fonctionnalités dans le fichier XML tandis que le Concepteur de packages est désactivé, ces éléments de projet et les fonctionnalités ne sont pas empaquetées.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Pour remplacer le fichier manifest de package en désactivant le Concepteur

1. Dans le **Concepteur de packages**, choisissez le **manifeste** onglet.

2. Développez le **modifier les Options** nœud, choisissez le **remplacement généré XML et modifier le manifeste dans l’éditeur XML** lier, puis choisissez le **Oui** bouton.

     Le modèle est mis à jour avec le fichier de manifeste de package actuel.

## <a name="enable-the-package-designer"></a>Activer le Concepteur de packages
 Vous pouvez réactiver le Concepteur de packages pour personnaliser le *manifest.xml* fichier.

#### <a name="to-re-enable-the-designer"></a>Pour réactiver le Concepteur

1. Dans le **Concepteur de packages**, choisissez le **rejet modifications du manifeste et réactivez le concepteur** lier, puis choisissez le **Oui** bouton.

     Le modèle est actualisée avec le texte d’origine, et les modifications au code XML sont perdues.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
