---
title: Spécifier des fichiers journaux détaillés (déploiements ClickOnce)
description: Découvrez comment spécifier les commentaires des journaux d’activité gérés par ClickOnce pour l’installation, l’initialisation, la mise à jour et la désinstallation d’un déploiement ClickOnce.
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
ms.openlocfilehash: 0da285cfef49bd495fbecf39131e49cacd0476a5
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350918"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Guide pratique pour spécifier des fichiers journaux détaillés pour les déploiements ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gère les fichiers journaux d’activité pour tous les déploiements. Ces journaux documentent les détails relatifs à l’installation, l’initialisation, la mise à jour et la désinstallation d’un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Pour augmenter les détails qui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] écrivent dans ces fichiers journaux, utilisez l’éditeur du Registre ( *regedit.exe* ) pour spécifier le niveau de détail.

> [!CAUTION]
> Si vous utilisez l’éditeur du registre de façon incorrecte, vous risquez de provoquer de sérieux problèmes qui peuvent nécessiter la réinstallation du système d’exploitation. Son utilisation est sous votre entière responsabilité.

 La procédure suivante décrit comment spécifier le niveau de détail pour [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les fichiers journaux de l’utilisateur actuel. Pour réduire le niveau de détail, supprimez cette valeur de registre.

### <a name="to-specify-verbose-log-files"></a>Pour spécifier des fichiers journaux détaillés

1. Ouvrez *Regedit.exe*.

2. Accédez au nœud **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3. Si nécessaire, créez une valeur de chaîne nommée `LogVerbosityLevel` .

4. Définissez la valeur de `LogVerbosityLevel` sur `1`.

## <a name="see-also"></a>Voir aussi
- [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)