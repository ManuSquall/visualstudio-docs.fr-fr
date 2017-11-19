---
title: "Création d’une Extension avec une fenêtre outil | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cda2d9bc4bde1c0bf9d9dd82c48864725f0e25f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-tool-window"></a>Création d’une Extension avec une fenêtre outil
Dans cette procédure, vous apprenez à utiliser le modèle de projet VSIX et **fenêtre de l’outil personnalisé** modèle d’élément pour créer une extension avec une fenêtre outil.  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Création d’une fenêtre outil  
  
1.  Créez un projet VSIX nommé **FirstWindow**. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Lorsque le projet s’ouvre, ajouter un modèle d’élément de fenêtre outil nommé **MyWindow**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **fenêtre de l’outil personnalisé**. Dans le **nom** au bas de la fenêtre, modifiez le nom de fichier de fenêtre outil à **MyWindow.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l’instance expérimentale, accédez à **affichage / autres fenêtres**.  
  
     Vous devez voir un élément de menu pour **MyWindow**. Cliquez dessus.  
  
     Vous devez voir une fenêtre outil avec le titre **MyWindow** et un message de bouton **Click Me !.**