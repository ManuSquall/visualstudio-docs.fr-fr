---
title: 'Procédure : Spécifier les fichiers journaux détaillés pour les déploiements ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3e9abdd886215582d2f4a05145ab9da5bd81151b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041358"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procédure : Spécifier des fichiers journaux détaillés pour les déploiements ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] conserve les fichiers de journaux d’activité pour tous les déploiements. Ces journaux documentent les détails relatifs à l’installation, l’initialisation, la mise à jour et la désinstallation une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Pour davantage de détails qui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] écritures à ces fichiers journaux, utilisez l’Éditeur du Registre (*regedit.exe*) pour spécifier le niveau de détail.  
  
> [!CAUTION]
>  L’utilisation incorrecte de l’Éditeur du Registre vous pouvez entraîner des problèmes sérieux pouvant vous obliger à réinstaller le système d’exploitation. Utilisez-le à vos risques et périls.  
  
 La procédure suivante décrit comment spécifier le niveau de détail pour [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichiers journaux pour l’utilisateur actuel. Pour réduire le niveau de détail, supprimez cette valeur de Registre.  
  
### <a name="to-specify-verbose-log-files"></a>Pour spécifier les fichiers journaux détaillés  
  
1.  Ouvrez *Regedit.exe*.  
  
2.  Accédez au nœud **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.  
  
3.  Si nécessaire, créez une nouvelle valeur de chaîne nommée `LogVerbosityLevel`.  
  
4.  Définissez la valeur de `LogVerbosityLevel` sur `1`.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)