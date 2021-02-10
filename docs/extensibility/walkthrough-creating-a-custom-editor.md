---
title: 'Procédure pas à pas : création d’un éditeur personnalisé | Microsoft Docs'
description: Découvrez comment le modèle de projet VSPackage peut créer un éditeur personnalisé simple en C++ à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a4ebcf99634012943ed0a7fd1a72b5d4852729e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931381"
---
# <a name="walkthrough-create-a-custom-editor"></a>Procédure pas à pas : création d’un éditeur personnalisé
Le modèle de projet VSPackage peut créer un éditeur personnalisé simple en C++. Le modèle de projet VSPackage ne prend plus en charge les projets C# ou Visual Basic. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Modèle de projet de package Visual Studio
 Vous pouvez trouver le modèle de projet de package Visual Studio dans la boîte de dialogue **nouveau projet** , sous le dossier **extensibilité C++** .

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Pour créer un VSPackage à l’aide du modèle de package Visual Studio

1. Créez un projet avec le modèle de package Visual Studio.

2. Sélectionnez l’option **éditeur personnalisé** , puis cliquez sur **suivant**. La page Options de l' **éditeur** s’affiche.

3. Tapez le nom de votre éditeur dans la zone nom de l' **éditeur** . Tapez l’extension de fichier que vous souhaitez associer à votre éditeur dans la zone **extension de fichier** . Votre éditeur est disponible pour les fichiers avec cette extension. L’extension de fichier est inscrite uniquement pour Visual Studio, et non pour Windows. Tapez le nom de fichier par défaut pour les nouveaux documents créés avec votre éditeur dans la zone **nom de fichier par défaut** .

4. Cliquez sur **Terminer** pour créer votre VSPackage dans le dossier que vous avez spécifié.

### <a name="to-test-your-custom-editor"></a>Pour tester votre éditeur personnalisé

1. Dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **fichier**.

2. Dans le volet **modèles installés** de la boîte de dialogue **nouveau fichier** , sélectionnez le modèle de fichier, puis le type de fichier que vous avez enregistré.

3. Cliquez sur **ouvrir** pour afficher et modifier le document.

     L’éditeur prend en charge les opérations couper-coller, Rechercher et remplacer, et les opérations d’ouverture et de chargement.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)
