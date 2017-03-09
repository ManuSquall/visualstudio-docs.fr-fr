---
title: "Erreur du compilateur CS1557 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1557"
ms.assetid: 1615e028-aeb7-4788-bd87-8e49e502d698
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1557
Impossible d’utiliser 'classe' pour la méthode Main, car il figure dans un autre fichier de sortie  
  
 L’option de compilateur [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) a été spécifiée pour un fichier de sortie dans une compilation à plusieurs fichiers de sortie. Toutefois, la classe n’a pas été trouvée dans le code source de la compilation \/main. Elle a été trouvée dans le fichier de code source d’un autre fichier de sortie de la compilation.