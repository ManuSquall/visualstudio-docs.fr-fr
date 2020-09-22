---
title: 'Procédure : définir un emplacement de fichier journal personnalisé pour les erreurs de déploiement ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a1b7c93e4b30bbfd373a5fad9d7001452d4f587
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839530"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Comment : définir l'emplacement d'un fichier journal personnalisé pour les erreurs de déploiement ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] conserve les fichiers journaux d’activation pour tous les déploiements. Ces journaux documentent les erreurs relatives à l’installation et à l’initialisation d’un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement. Par défaut, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crée un fichier journal pour chaque activation de déploiement. Il stocke ces fichiers journaux dans le dossier Temporary Internet Files. Le fichier journal d’un déploiement est présenté à l’utilisateur lorsqu’un échec d’activation se produit et que l’utilisateur clique sur **Détails** dans la boîte de dialogue d’erreur qui s’affiche.  
  
 Vous pouvez modifier ce comportement pour un client spécifique à l’aide de l’éditeur du Registre (**regedit.exe**) pour définir un chemin d’accès au fichier journal personnalisé. Dans ce cas, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] journalise les réussites et échecs d’activation pour tous les déploiements dans un seul fichier.  
  
> [!CAUTION]
> L’utilisation incorrecte de l’Éditeur du Registre peut entraîner des problèmes graves dont la résolution peut impliquer la réinstallation du système d’exploitation. Son utilisation est sous votre entière responsabilité.  
  
> [!NOTE]
> Vous devez tronquer ou supprimer le fichier journal occasionnellement pour éviter qu’il ne devienne trop volumineux.  
  
 La procédure suivante décrit comment définir un emplacement de fichier journal personnalisé pour un seul client.  
  
### <a name="to-set-a-custom-log-file-location"></a>Pour définir un emplacement de fichier journal personnalisé  
  
1. Ouvrez **Regedit.exe**.  
  
2. Accédez au nœud `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Définissez la valeur de chaîne `LogFilePath` sur le chemin d’accès complet et le nom de fichier de votre emplacement de journal personnalisé préféré.  
  
     Cet emplacement doit se trouver dans un répertoire auquel l’utilisateur a accès en écriture. Par exemple, sur Windows Vista, créez la structure de dossiers suivante et définissez `LogFilePath` sur C:\Users \\<nom d’utilisateur \> \Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
