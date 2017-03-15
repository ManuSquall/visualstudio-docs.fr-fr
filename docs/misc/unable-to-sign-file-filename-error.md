---
title: "Impossible de signer le fichier &#39;&lt;nom_fichier&gt;&#39;&#160;: &lt;erreur&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31028"
  - "vbc31028"
helpviewer_keywords: 
  - "BC31028"
ms.assetid: 2cb22e75-5ee2-4e07-afc0-680a0bd543d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de signer le fichier &#39;&lt;nom_fichier&gt;&#39;&#160;: &lt;erreur&gt;
Une erreur s’est produite lors de la tentative de signature du fichier spécifié. Cette erreur peut se produire pour plusieurs raisons :  
  
-   Autorisations insuffisantes.  
  
-   Fichiers système nécessaires à la signature Authenticode manquants.  
  
-   Référence à un fichier de clé privée ou à un certificat inexistant.  
  
-   Orthographe incorrecte d’un nom de fichier ou d’une URL.  
  
 **ID d’erreur :** BC31028  
  
### Pour corriger cette erreur  
  
1.  Entrez correctement le nom de fichier du certificat et celui de la clé privée.  
  
2.  Si vous utilisez la signature Authenticode, vérifiez que les fichiers Signcode.exe et Javasign.dll sont présents et que leur attribut en lecture seule n’est pas défini.  
  
3.  Vérifiez que vous disposez de l’autorisation `Write` sur le fichier.  
  
## Voir aussi  
 [File Signing Tool \(Signcode.exe\)](http://msdn.microsoft.com/fr-fr/2d299154-34ea-41ba-ad12-17075bb7e1db)   
 [Deployment and Authenticode Signing](http://msdn.microsoft.com/fr-fr/ecc3f059-da2e-445b-9b87-5b2978e2f8b2)