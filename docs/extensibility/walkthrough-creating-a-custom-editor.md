---
title: 'Procédure pas à pas : Création d’un éditeur personnalisé | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9110e1c2ac6c39898f7dbbd6f9f4412ebcba278
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497435"
---
# <a name="walkthrough-create-a-custom-editor"></a>Procédure pas à pas : Créer un éditeur personnalisé
Le modèle de projet VSPackage peut créer un éditeur personnalisé simple en C++. Le modèle de projet VSPackage n’est plus prend en charge que les projets c# ou Visual Basic. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Le modèle de projet de Package Visual Studio  
 Vous pouvez trouver le modèle de projet de Package Visual Studio dans le **nouveau projet** boîte de dialogue sous la **C++ extensibilité** dossier.  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Pour créer un VSPackage à l’aide du modèle de package Visual Studio  
  
1.  Créez un projet avec le modèle de Package Visual Studio.  
  
2.  Sélectionnez le **éditeur personnalisé** , cliquez sur **suivant**. Le **Options de l’éditeur** page s’affiche.  
  
3.  Tapez le nom de votre éditeur dans le **nom d’éditeur** boîte. Tapez l’extension de fichier que vous souhaitez associer à votre éditeur dans le **Extension de fichier** boîte. Votre éditeur est disponible pour les fichiers avec cette extension. L’extension de fichier est enregistrée pour Visual Studio uniquement, pas pour Windows. Tapez le nom de fichier par défaut pour les nouveaux documents créés avec votre éditeur dans le **nom de fichier par défaut** boîte.  
  
4.  Cliquez sur **Terminer** pour créer votre VSPackage dans le dossier que vous avez spécifié.  
  
### <a name="to-test-your-custom-editor"></a>Pour tester votre éditeur personnalisé  
  
1.  Sur le **fichier** menu, pointez sur **New** puis cliquez sur **fichier**.  
  
2.  Dans le **modèles installés** volet de la **nouveau fichier** boîte de dialogue, sélectionnez le modèle de fichier, puis le fichier de type vous inscrit.  
  
3.  Cliquez sur **Open** pour afficher et modifier le document.  
  
     L’éditeur prend en charge les opérations couper-coller, rechercher et remplacer et open-and-load.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)