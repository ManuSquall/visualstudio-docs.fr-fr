---
title: 'Comment : définir un emplacement de fichier journal personnalisé pour les erreurs de déploiement ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: e4108287e120eabb4c8fc38d1dc29f2a81ea3d47
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207699"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Comment : définir l'emplacement d'un fichier journal personnalisé pour les erreurs de déploiement ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] conserve les fichiers de journaux d’activation pour tous les déploiements. Ces journaux documentent toutes les erreurs relatives à l’installation et l’initialisation une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement. Par défaut, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crée un fichier journal pour chaque activation de déploiement. Elle stocke ces fichiers journaux dans le dossier fichiers Internet temporaires. Le fichier journal pour un déploiement s’affiche à l’utilisateur lorsqu’un échec d’activation se produit, et l’utilisateur clique sur **détails** dans la boîte de dialogue d’erreur.  
  
 Vous pouvez modifier ce comportement pour un client spécifique à l’aide de l’Éditeur du Registre (**regedit.exe**) pour définir un chemin d’accès du fichier journal personnalisé. Dans ce cas, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] enregistre les réussites et l’activation échecs pour tous les déploiements dans un seul fichier.  
  
> [!CAUTION]
>  L’utilisation incorrecte de l’Éditeur du Registre vous pouvez entraîner des problèmes sérieux pouvant vous obliger à réinstaller votre système d’exploitation. Utilisez-le à vos risques et périls.  
  
> [!NOTE]
>  Vous devrez tronquez ou supprimez le fichier journal occasionnellement pour l’empêcher de devenir trop volumineux.  
  
 La procédure suivante décrit comment définir un emplacement de fichier journal personnalisé pour un seul client.  
  
### <a name="to-set-a-custom-log-file-location"></a>Pour définir un emplacement de fichier journal personnalisé  
  
1.  Ouvrez **Regedit.exe**.  
  
2.  Accédez au nœud `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Définissez la valeur de chaîne `LogFilePath` pour le chemin d’accès complet et le nom de votre emplacement de journal personnalisé favori.  
  
     Cet emplacement doit être dans un répertoire auquel l’utilisateur a accès en écriture. Par exemple, sur Windows Vista, créez la structure de dossier suivante et définissez `LogFilePath` à C:\Users\\< nom d’utilisateur\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)





