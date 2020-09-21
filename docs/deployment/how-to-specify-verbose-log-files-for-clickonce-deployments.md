---
title: Spécifier des fichiers journaux détaillés (déploiements ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54c90f6a544607e78dd8f294bfc307bc87377b70
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808709"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Guide pratique pour spécifier des fichiers journaux détaillés pour les déploiements ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gère les fichiers journaux d’activité pour tous les déploiements. Ces journaux documentent les détails relatifs à l’installation, l’initialisation, la mise à jour et la désinstallation d’un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Pour augmenter les détails qui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] écrivent dans ces fichiers journaux, utilisez l’éditeur du Registre (*regedit.exe*) pour spécifier le niveau de détail.

> [!CAUTION]
> Si vous utilisez l’éditeur du registre de façon incorrecte, vous risquez de provoquer de sérieux problèmes qui peuvent nécessiter la réinstallation du système d’exploitation. Son utilisation est sous votre entière responsabilité.

 La procédure suivante décrit comment spécifier le niveau de détail pour [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les fichiers journaux de l’utilisateur actuel. Pour réduire le niveau de détail, supprimez cette valeur de registre.

### <a name="to-specify-verbose-log-files"></a>Pour spécifier des fichiers journaux détaillés

1. Ouvrez *Regedit.exe*.

2. Accédez au nœud **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment**.

3. Si nécessaire, créez une valeur de chaîne nommée `LogVerbosityLevel` .

4. Définissez la valeur de `LogVerbosityLevel` sur `1`.

## <a name="see-also"></a>Voir aussi
- [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)