---
title: La commande DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5f0eceeb4253460c17a52ebb8ec4082b9a743c70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963801"
---
# <a name="the-dsltexttransform-command"></a>La commande DslTextTransform
DslTextTransform.cmd est un script qui appelle TextTransform.exe et s’exécute avec les options courantes. Vous pouvez utiliser DslTextTransformation.cmd pour automatiser une build nocturne de votre [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projets. Pour plus d’informations, consultez [génération de fichiers avec l’utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd se trouve dans le répertoire suivant :

 **\<Chemin d’Installation de Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Vous pouvez spécifier les arguments suivants en tant qu’entrée à DslTextTransform.cmd :

- Le répertoire de sortie du projet de modèle de domaine.

- Le répertoire de sortie du projet de définition de concepteur.

- L’emplacement du fichier de modèle de texte.

  DslTextTransform.cmd traite le fichier de modèle de texte spécifié à l’aide des processeurs de directive par défaut et les assemblys. Si vous créez des processeurs de directive personnalisés, vous pouvez créer votre propre fichier de commandes qui appelle TextTransform.exe. Dans ce fichier de commandes, vous pouvez spécifier vos assemblys et les processeurs de directive personnalisés associés.