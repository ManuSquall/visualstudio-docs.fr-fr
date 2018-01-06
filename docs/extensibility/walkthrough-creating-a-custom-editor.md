---
title: "Procédure pas à pas : Création d’un éditeur personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9e8ea75cb96b36f885a55cbf9f174394379dc05a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-editor"></a>Procédure pas à pas : Création d’un éditeur personnalisé
Le modèle de projet VSPackage peut créer un éditeur personnalisé simple en C++.  Le modèle de projet VSPackage ne prend plus en projets c# ou Visual Basic. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Le modèle de projet de Package Visual Studio  
 Le modèle de projet de Package Visual Studio peut être trouvé dans le **nouveau projet** boîte de dialogue dans le dossier de l’extensibilité de C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Pour créer un VSPackage à l’aide du modèle de Package Visual Studio  
  
1.  Créez un projet avec le modèle de Package Visual Studio.  
  
2.  Sélectionnez le **éditeur personnalisé** , puis cliquez sur **suivant**. Le **Options de l’éditeur** page s’affiche.  
  
3.  Tapez le nom de votre éditeur dans le **nom de l’éditeur** boîte. Tapez l’extension de fichier que vous souhaitez associer à votre éditeur dans le **Extension de fichier** boîte. Votre éditeur est disponible pour les fichiers avec cette extension. L’extension de fichier est enregistrée pour Visual Studio uniquement, pas pour Windows. Tapez le nom de fichier par défaut pour les documents créés dans votre éditeur dans le **nom de fichier par défaut** boîte.  
  
4.  Cliquez sur **Terminer** pour créer votre VSPackage dans le dossier que vous avez spécifié.  
  
### <a name="to-test-your-custom-editor"></a>Pour tester votre éditeur personnalisé  
  
1.  Sur le **fichier** menu, pointez sur **nouveau** puis cliquez sur **fichier**.  
  
2.  Dans le **modèles installés** volet de la **nouveau fichier** boîte de dialogue, sélectionnez le modèle de fichier, puis le fichier de type que vous venez d’enregistrer.  
  
3.  Cliquez sur **ouvrir** pour afficher et modifier le document.  
  
     L’éditeur prend en charge les opérations de couper-coller, rechercher et remplacer et ouvrir et de charge.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)