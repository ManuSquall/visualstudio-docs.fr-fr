---
title: Création d’une extension avec une fenêtre outil | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431847"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Création d’une extension avec une fenêtre d’outil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure, vous allez apprendre à utiliser le modèle de projet VSIX et le modèle d’élément de **fenêtre outil personnalisé** pour créer une extension avec une fenêtre outil.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Création d’une fenêtre outil  
  
1. Créez un projet VSIX nommé **FirstWindow**. Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** sous **Visual C#/extensibilité**.  
  
2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de fenêtre outil nommé **FirstWindow**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C#/extensibilité** et sélectionnez **fenêtre outil personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom de fichier de la fenêtre outil par **FirstWindow.cs**.  
  
3. Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4. Dans l’instance expérimentale, accédez à **affichage/autres fenêtres**.  
  
     Vous devez voir un élément de menu pour **FirstWindow**. Cliquez dessus.  
  
     Vous devez voir une fenêtre outil avec le titre **FirstWindow** et un bouton indiquant **Click Me !.**
