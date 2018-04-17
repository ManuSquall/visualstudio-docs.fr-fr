---
title: La commande DslTextTransform | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 11fb12f3716fe9f8b5fee13a7eecd88ee107ff45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="the-dsltexttransform-command"></a>La commande DslTextTransform
DslTextTransform.cmd est un script qui appelle TextTransform.exe et elle s’exécute avec les options courantes. Vous pouvez utiliser DslTextTransformation.cmd pour automatiser une build nocturne de votre [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projets. Pour plus d’informations, consultez [génération de fichiers avec l’utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd se trouve dans le répertoire suivant :  
  
 **\<Chemin d’Installation de Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**  
  
 Vous pouvez spécifier les arguments suivants en tant qu’entrée à DslTextTransform.cmd :  
  
-   Le répertoire de sortie du projet de modèle de domaine.  
  
-   Le répertoire de sortie du projet de définition de concepteur.  
  
-   L’emplacement du fichier de modèle de texte.  
  
 DslTextTransform.cmd traite le fichier de modèle de texte spécifié en utilisant les processeurs de directive par défaut et les assemblys. Si vous créez des processeurs de directive personnalisés, vous pouvez créer votre propre fichier de commandes qui appelle TextTransform.exe. Dans ce fichier de commandes, vous pouvez spécifier vos assemblys et les processeurs de directive personnalisés associés.