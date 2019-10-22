---
title: Commande DslTextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658463"
---
# <a name="the-dsltexttransform-command"></a>La commande DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform. cmd est un script qui appelle TextTransform. exe et l’exécute avec des options communes. Vous pouvez utiliser DslTextTransformation. cmd pour automatiser une génération nocturne de vos projets [!INCLUDE[dsl](../includes/dsl-md.md)]. Pour plus d’informations, consultez [génération de fichiers avec l’utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd se trouve dans le répertoire suivant :

 **Chemin d’installation du kit de développement logiciel (SDK) \<Visual Studio > \VisualStudioIntegration\Tools\Bin**

 Vous pouvez spécifier les arguments suivants comme entrée pour DslTextTransform. cmd :

- Répertoire de sortie du projet de modèle de domaine.

- Répertoire de sortie du projet de définition de concepteur.

- Emplacement du fichier de modèle de texte.

  DslTextTransform. cmd traite le fichier de modèle de texte spécifié à l’aide des processeurs et des assemblys de directive par défaut. Si vous créez des processeurs de directive personnalisés, vous pouvez créer votre propre fichier de commandes qui appelle TextTransform. exe. Dans ce fichier de commandes, vous pouvez spécifier vos assemblys et les processeurs de directive personnalisés associés.
