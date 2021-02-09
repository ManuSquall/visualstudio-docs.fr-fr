---
title: Lorsque les charges utiles du package sont modifiées après une mise en production
description: Lorsque vous créez une disposition, découvrez comment déterminer si les charges utiles du package ont été modifiées après la livraison d’une mise en production.
ms.date: 05/22/2019
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bd0013df051def28c57552c0aeb733888d55e9b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905548"
---
# <a name="package-payload-changes"></a>Changements de charge utile de package

Certaines charges utiles du package peuvent être modifiées après la livraison d’une mise en production. Lorsque vous ou quelqu'un d’autre crée une disposition, ce comportement peut entraîner différent contenu de la disposition, en fonction du moment de création d’une disposition.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Vérifier qu’une disposition inclut des modifications de charge utile du package

Voici comment déterminer si la disposition qui a été créée précédemment a acquis les charges utiles du package qui ont été modifiées après la livraison de la mise en production :

1. Ouvrez le journal d’installation. Le journal est généralement à `%TEMP%\dd_setup_[date].log` où `[date]` est la moment du démarrage de l’opération de disposition au format `yyyyMMddHHmmss`.

2. Recherchez une ligne dans le journal structurée comme le texte suivant :

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Ensuite, recherchez les lignes plus loin dans le journal qui indiquent que le téléchargement a réussi pour le [chemin d’accès]. Elles doivent ressembler au texte suivant :

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Voir aussi

* [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
