---
title: "Comment : spécifier des fichiers journaux détaillés pour les déploiements ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2fccf1b0c9d7a67ca1eeb6058c1294cea2f2005a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Comment : spécifier des fichiers journaux détaillés pour les déploiements ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]conserve les fichiers journaux d’activité pour tous les déploiements. Ces journaux documentent les détails relatifs à l’installation, l’initialisation, la mise à jour et la désinstallation une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Pour davantage de détails qui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] écrit dans ces fichiers journaux, utilisez l’Éditeur du Registre (**regedit.exe**) pour spécifier le niveau de détail.  
  
> [!CAUTION]
>  Si vous utilisez l’Éditeur du Registre correctement, vous pouvez provoquer des problèmes sérieux pouvant vous obliger à réinstaller le système d’exploitation. Utilisez-le à vos risques et périls.  
  
 La procédure suivante décrit comment spécifier le niveau de détail pour [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichiers journaux pour l’utilisateur actuel. Pour réduire le niveau de détail, supprimez cette valeur de Registre.  
  
### <a name="to-specify-verbose-log-files"></a>Pour spécifier les fichiers journaux détaillés  
  
1.  Ouvrez **Regedit.exe**.  
  
2.  Accédez au nœud `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Si nécessaire, créez une nouvelle valeur de chaîne nommée `LogVerbosityLevel`.  
  
4.  Définir le `LogVerbosityLevel` valeur `1`.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)