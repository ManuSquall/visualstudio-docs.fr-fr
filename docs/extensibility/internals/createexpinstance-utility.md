---
title: "Utilitaire de CreateExpInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "builds expérimentales"
  - "ruche expérimentale"
  - "instance expérimentale"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Utilitaire de CreateExpInstance
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez l’utilitaire CreateExpInstance pour créer, réinitialiser, ou supprimer une instance expérimentale de Visual Studio. Vous pouvez utiliser l’instance expérimentale pour déboguer et tester des extensions Visual Studio sans modifier le produit sous\-jacent.  
  
## Syntaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### Paramètres  
 \/ Create  
 Crée l’instance expérimentale.  
  
 \/ Reset  
 Supprime l’instance expérimentale et crée un nouveau.  
  
 \/Clean  
 Supprime l’instance expérimentale.  
  
 \/ VSInstance  
 Le nom du répertoire qui contient l’instance de Visual Studio de base à copier.  
  
 \/ RootSuffix  
 Le suffixe à ajouter au nom du répertoire d’instance expérimentale.  
  
## Notes  
 Lorsque vous travaillez sur une extension de Visual Studio, vous pouvez appuyer sur F5 pour ouvrir l’instance expérimentale par défaut et installer l’extension actuelle. Si aucune instance expérimentale n’est disponible, Visual Studio crée un objet qui contient les paramètres par défaut.  
  
 L’emplacement par défaut de l’instance expérimentale varie selon le numéro de version de Visual Studio. Par exemple, pour Visual Studio 2015, l’emplacement est %localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ tous les fichiers dans l’emplacement du répertoire sont considérées comme faisant partie de cette instance. Toute instance expérimentale supplémentaire ne sera pas chargé par Visual Studio, sauf si le nom du répertoire est modifié à l’emplacement par défaut.  
  
 Visual Studio n’a pas accès du Registre système lors de l’ouverture de l’instance expérimentale. Ceci diffère des versions antérieures de Visual Studio, qui ont utilisé une version expérimentale de la ruche du Registre.  
  
 L’utilitaire CreateExpInstance remplace l’utilitaire VsRegEx.  
  
 L’exemple suivant réinitialise l’instance expérimentale de la valeur par défaut de Visual Studio.  
  
 **\/ Reset CreateExpInstance.exe \/VSInstance \= 14.0 \/RootSuffix \= Exp**  
  
## Voir aussi  
 [Publication d’un produit](../../misc/releasing-a-visual-studio-integration-product.md)