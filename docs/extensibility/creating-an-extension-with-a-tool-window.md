---
title: Création d’une Extension avec une fenêtre outil | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f918a5b8b48a7b9553cf3ca2e6c8fe9d38fbc9b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-tool-window"></a>Création d’une Extension avec une fenêtre outil
Dans cette procédure, vous apprenez à utiliser le modèle de projet VSIX et **fenêtre de l’outil personnalisé** modèle d’élément pour créer une extension avec une fenêtre outil.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Création d’une fenêtre outil  
  
1.  Créez un projet VSIX nommé **FirstWindow**. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Lorsque le projet s’ouvre, ajouter un modèle d’élément de fenêtre outil nommé **MyWindow**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **fenêtre de l’outil personnalisé**. Dans le **nom** au bas de la fenêtre, modifiez le nom de fichier de fenêtre outil à **MyWindow.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l’instance expérimentale, accédez à **affichage / autres fenêtres**.  
  
     Vous devez voir un élément de menu pour **MyWindow**. Cliquez dessus.  
  
     Vous devez voir une fenêtre outil avec le titre **MyWindow** et un message de bouton **Click Me !.**