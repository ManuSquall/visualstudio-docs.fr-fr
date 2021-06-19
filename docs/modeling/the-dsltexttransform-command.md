---
title: La commande DslTextTransform
description: Découvrez que DslTextTransform. cmd est un script qui appelle TextTransform.exe et l’exécute avec des options communes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65d1e1d02c5b7d13c2e86343c6307306542d00e2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388644"
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
