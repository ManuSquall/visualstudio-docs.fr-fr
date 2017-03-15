---
title: "La commande DslTextTransform | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domain-Specific Language, commandes"
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 30
---
# La commande DslTextTransform
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DslTextTransform.cmd est un script qui appelle TextTransform.exe et s’exécute avec les options courantes. Vous pouvez utiliser DslTextTransformation.cmd pour automatiser une build nocturne de votre [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projets. Pour plus d’informations, consultez [génération de fichiers avec l’utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd se trouve dans le répertoire suivant :  
  
 **\< chemin d’Installation de visual Studio SDK>\VisualStudioIntegration\Tools\Bin**  
  
 Vous pouvez spécifier les arguments suivants en tant qu’entrée à DslTextTransform.cmd :  
  
-   Le répertoire de sortie du projet de modèle de domaine.  
  
-   Le répertoire de sortie du projet de définition de concepteur.  
  
-   L’emplacement du fichier de modèle de texte.  
  
 DslTextTransform.cmd traite le fichier de modèle de texte spécifié en utilisant les processeurs de directive par défaut et les assemblys. Si vous créez des processeurs de directive personnalisés, vous pouvez créer votre propre fichier de commandes qui appelle TextTransform.exe. Dans ce fichier de commandes, vous pouvez spécifier vos assemblys et les processeurs de directive personnalisés associés.