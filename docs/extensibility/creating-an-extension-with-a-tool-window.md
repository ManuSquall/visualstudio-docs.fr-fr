---
title: "Cr&#233;ation d&#39;une Extension avec une fen&#234;tre outil | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Cr&#233;ation d&#39;une Extension avec une fen&#234;tre outil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans cette procédure, vous apprenez à utiliser le modèle de projet VSIX et **fenêtre de l'outil personnalisé** modèle d'élément pour créer une extension avec une fenêtre outil.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Création d'une fenêtre outil  
  
1.  Créez un projet VSIX nommé **FirstWindow**. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\# \/ extensibilité**.  
  
2.  Lorsque le projet s'ouvre, ajoutez un modèle d'élément de fenêtre outil nommé **FirstWindow**. Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **fenêtre de l'outil personnalisé**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de fenêtre outil à **FirstWindow.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L'instance expérimentale de Visual Studio s'affiche. Pour plus d'informations sur l'instance expérimentale, consultez [L'Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l'instance expérimentale, accédez à **affichage \/ autres fenêtres**.  
  
     Vous devez voir un élément de menu pour **FirstWindow**. Cliquez dessus.  
  
     Vous devez voir une fenêtre outil avec le titre **FirstWindow** et un message bouton **Click Me\!.**