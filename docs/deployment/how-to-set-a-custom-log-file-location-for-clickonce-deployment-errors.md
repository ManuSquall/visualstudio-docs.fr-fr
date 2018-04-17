---
title: 'Comment : définir un emplacement de fichier journal personnalisé pour les erreurs de déploiement ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a54946f5750e901c937dd91772eb7d7ecb740e48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Comment : définir l'emplacement d'un fichier journal personnalisé pour les erreurs de déploiement ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] conserve les fichiers de journaux de l’activation de tous les déploiements. Ces journaux documentent toutes les erreurs relatives à l’installation et l’initialisation un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Par défaut, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crée un fichier journal pour chaque activation de déploiement. Elle stocke ces fichiers journaux dans le dossier fichiers Internet temporaires. Le fichier journal pour un déploiement s’affiche à l’utilisateur lorsqu’un échec d’activation se produit, et que l’utilisateur clique sur **détails** dans la boîte de dialogue d’erreur.  
  
 Vous pouvez modifier ce comportement pour un client spécifique à l’aide de l’Éditeur du Registre (**regedit.exe**) pour définir un chemin d’accès du fichier journal personnalisé. Dans ce cas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] enregistre les réussites et l’activation échecs pour tous les déploiements dans un seul fichier.  
  
> [!CAUTION]
>  Si vous utilisez l’Éditeur du Registre correctement, vous pouvez provoquer des problèmes sérieux pouvant vous obliger à réinstaller votre système d’exploitation. Utilisez-le à vos risques et périls.  
  
> [!NOTE]
>  Vous devrez tronquez ou supprimez le fichier journal occasionnellement pour l’empêcher de devenir trop volumineux.  
  
 La procédure suivante décrit comment définir un emplacement de fichier journal personnalisé pour un seul client.  
  
### <a name="to-set-a-custom-log-file-location"></a>Pour définir un emplacement de fichier journal personnalisé  
  
1.  Ouvrez **Regedit.exe**.  
  
2.  Accédez au nœud `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Définir la valeur de chaîne `LogFilePath` pour le chemin d’accès complet et le nom de votre emplacement de journal personnalisé favori.  
  
     Cet emplacement doit être dans un répertoire auquel l’utilisateur a accès en écriture. Par exemple, sur Windows Vista, créez la structure de dossier suivante et définir `LogFilePath` à C:\Users\\< nom d’utilisateur\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)