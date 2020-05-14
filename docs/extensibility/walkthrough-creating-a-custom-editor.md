---
title: 'Procédure pas à pas : Création d’un éditeur personnalisé (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697674"
---
# <a name="walkthrough-create-a-custom-editor"></a>Procédure pas à pas : Créez un éditeur personnalisé
Le modèle de projet VSPackage peut créer un simple éditeur personnalisé en C. Le modèle de projet VSPackage ne prend plus en charge les projets C ou Visual Basic. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Le modèle de projet Visual Studio Package
 Vous pouvez trouver le modèle de projet Visual Studio Package dans le dialogue **new Project** sous le dossier **Extensibility.**

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Pour créer un VSPackage à l’aide du modèle de paquet Visual Studio

1. Créez un projet avec le modèle Visual Studio Package.

2. Sélectionnez l’option **Éditeur personnalisé** et cliquez sur **Next**. La page **Options d’éditeur** apparaît.

3. Tapez le nom de votre éditeur dans la boîte **nom de l’éditeur.** Tapez l’extension de fichier que vous souhaitez être associée à votre éditeur dans la boîte **d’extension de fichiers.** Votre éditeur est disponible pour les fichiers avec cette extension. L’extension de fichier est enregistrée pour Visual Studio seulement, pas pour Windows. Tapez le nom de fichier par défaut pour les nouveaux documents créés avec votre éditeur dans la boîte **nom de fichier par défaut.**

4. Cliquez sur **Terminer** pour créer votre VSPackage dans le dossier que vous avez spécifié.

### <a name="to-test-your-custom-editor"></a>Pour tester votre éditeur personnalisé

1. Sur le menu **du fichier,** pointez vers **New** puis cliquez sur **Fichier**.

2. Dans le volet **Modèles installés** de la boîte de dialogue Du **nouveau fichier,** sélectionnez le modèle de fichier, puis le type de fichier que vous avez enregistré.

3. Cliquez **sur Ouvert** pour afficher et modifier le document.

     L’éditeur prend en charge les opérations de coupe et de pâte, de recherche et de remplacement et d’ouverture et de charge.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)
