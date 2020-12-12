---
title: La commande DslTextTransform
description: Découvrez que DslTextTransform. cmd est un script qui appelle TextTransform.exe et l’exécute avec des options communes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74f87f735f5ad6864082046327bc852d5d43fdb6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362715"
---
# <a name="the-dsltexttransform-command"></a>La commande DslTextTransform
DslTextTransform. cmd est un script qui appelle TextTransform.exe et l’exécute avec des options communes. Vous pouvez utiliser DslTextTransformation. cmd pour automatiser une génération nocturne de vos [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projets. Pour plus d’informations, consultez [génération de fichiers avec l’utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd se trouve dans le répertoire suivant :

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Vous pouvez spécifier les arguments suivants comme entrée pour DslTextTransform. cmd :

- Répertoire de sortie du projet de modèle de domaine.

- Répertoire de sortie du projet de définition de concepteur.

- Emplacement du fichier de modèle de texte.

  DslTextTransform. cmd traite le fichier de modèle de texte spécifié à l’aide des processeurs et des assemblys de directive par défaut. Si vous créez des processeurs de directive personnalisés, vous pouvez créer votre propre fichier de commandes qui appelle TextTransform.exe. Dans ce fichier de commandes, vous pouvez spécifier vos assemblys et les processeurs de directive personnalisés associés.
