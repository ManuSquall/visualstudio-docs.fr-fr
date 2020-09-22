---
title: Guide pratique pour spécifier des fichiers journaux détaillés pour les déploiements ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840165"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Comment : spécifier des fichiers journaux détaillés pour les déploiements ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] gère les fichiers journaux d’activité pour tous les déploiements. Ces journaux documentent les détails relatifs à l’installation, l’initialisation, la mise à jour et la désinstallation d’un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement. Pour augmenter les détails qui [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] écrivent dans ces fichiers journaux, utilisez l’éditeur du Registre (**regedit.exe**) pour spécifier le niveau de détail.  
  
> [!CAUTION]
> Si vous utilisez l’éditeur du registre de façon incorrecte, vous risquez de provoquer de sérieux problèmes qui peuvent nécessiter la réinstallation du système d’exploitation. Son utilisation est sous votre entière responsabilité.  
  
 La procédure suivante décrit comment spécifier le niveau de détail pour [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] les fichiers journaux de l’utilisateur actuel. Pour réduire le niveau de détail, supprimez cette valeur de registre.  
  
### <a name="to-specify-verbose-log-files"></a>Pour spécifier des fichiers journaux détaillés  
  
1. Ouvrez **Regedit.exe**.  
  
2. Accédez au nœud `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Si nécessaire, créez une valeur de chaîne nommée `LogVerbosityLevel` .  
  
4. Définissez la valeur de `LogVerbosityLevel` sur `1`.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
