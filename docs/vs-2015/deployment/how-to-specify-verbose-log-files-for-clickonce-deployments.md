---
title: 'Comment : spécifier les fichiers journaux détaillés pour les déploiements ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: b30260267fca5b7de16316e84082fc3b464f7deb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501947"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Comment : spécifier des fichiers journaux détaillés pour les déploiements ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : spécifier les fichiers journaux détaillés pour les déploiements ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-verbose-log-files-for-clickonce-deployments).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] conserve les fichiers de journaux d’activité pour tous les déploiements. Ces journaux documentent les détails relatifs à l’installation, l’initialisation, la mise à jour et la désinstallation une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement. Pour davantage de détails qui [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] écritures à ces fichiers journaux, utilisez l’Éditeur du Registre (**regedit.exe**) pour spécifier le niveau de détail.  
  
> [!CAUTION]
>  L’utilisation incorrecte de l’Éditeur du Registre vous pouvez entraîner des problèmes sérieux pouvant vous obliger à réinstaller le système d’exploitation. Utilisez-le à vos risques et périls.  
  
 La procédure suivante décrit comment spécifier le niveau de détail pour [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fichiers journaux pour l’utilisateur actuel. Pour réduire le niveau de détail, supprimez cette valeur de Registre.  
  
### <a name="to-specify-verbose-log-files"></a>Pour spécifier les fichiers journaux détaillés  
  
1.  Ouvrez **Regedit.exe**.  
  
2.  Accédez au nœud `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Si nécessaire, créez une nouvelle valeur de chaîne nommée `LogVerbosityLevel`.  
  
4.  Définir le `LogVerbosityLevel` valeur `1`.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)



