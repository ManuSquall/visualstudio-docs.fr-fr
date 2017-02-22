---
title: "Proc&#233;dure pas &#224; pas : Cr&#233;ation d&#39;un &#233;diteur personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), personnalisés - création"
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Proc&#233;dure pas &#224; pas : Cr&#233;ation d&#39;un &#233;diteur personnalis&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le modèle de projet VSPackage peut créer un éditeur personnalisé simple en C\+\+.  Le modèle de projet VSPackage plus prend en charge les projets Visual c\# ou Visual Basic. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Le modèle de projet de Package Visual Studio  
 Le modèle de projet de Package Visual Studio figurent dans le **Nouveau projet** boîte de dialogue dans le dossier de l'extensibilité de C\+\+  
  
### Pour créer un VSPackage en utilisant le modèle de Package Visual Studio  
  
1.  Créez un projet avec le modèle de Package Visual Studio.  
  
2.  Sélectionnez le **éditeur personnalisé** puis cliquez sur **Suivant**. Le **Options de l'éditeur** page s'affiche.  
  
3.  Tapez le nom de votre éditeur dans le **nom d'éditeur** boîte. Tapez l'extension de fichier que vous souhaitez associer à votre éditeur dans le **Extension de fichier** boîte. Votre éditeur est disponible pour les fichiers portant cette extension. L'extension de fichier est enregistrée pour Visual Studio uniquement, pas pour Windows. Tapez le nom de fichier par défaut pour les documents créés dans votre éditeur dans le **nom de fichier par défaut** boîte.  
  
4.  Cliquez sur **Terminer** pour créer votre VSPackage dans le dossier que vous avez spécifié.  
  
### Pour tester votre éditeur personnalisé  
  
1.  Sur le **fichier** menu, pointez sur **nouveau** puis **fichier**.  
  
2.  Dans le **modèles installés** volet de la **nouveau fichier** boîte de dialogue, sélectionnez le modèle de fichier, puis le fichier type que vous venez d'enregistrer.  
  
3.  Cliquez sur **Open** pour afficher et modifier le document.  
  
     L'éditeur prend en charge les opérations couper\-coller, rechercher et remplacer et open\-and\-load.  
  
## Voir aussi  
 [Packages VS](../extensibility/internals/vspackages.md)