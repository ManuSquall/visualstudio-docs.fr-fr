---
title: Définir l’emplacement du fichier journal personnalisé (erreurs de déploiement ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5b5cf73a685eb68e389e6531022200acbefbfd2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809740"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Guide pratique pour définir l’emplacement d’un fichier journal personnalisé pour les erreurs de déploiement ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] conserve les fichiers journaux d’activation pour tous les déploiements. Ces journaux documentent les erreurs relatives à l’installation et à l’initialisation d’un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Par défaut, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crée un fichier journal pour chaque activation de déploiement. Il stocke ces fichiers journaux dans le dossier Temporary Internet Files. Le fichier journal d’un déploiement est présenté à l’utilisateur lorsqu’un échec d’activation se produit et que l’utilisateur clique sur **Détails** dans la boîte de dialogue d’erreur qui s’affiche.

 Vous pouvez modifier ce comportement pour un client spécifique à l’aide de l’éditeur du Registre (**regedit.exe**) pour définir un chemin d’accès au fichier journal personnalisé. Dans ce cas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] journalise les réussites et échecs d’activation pour tous les déploiements dans un seul fichier.

> [!CAUTION]
> L’utilisation incorrecte de l’Éditeur du Registre peut entraîner des problèmes graves dont la résolution peut impliquer la réinstallation du système d’exploitation. Son utilisation est sous votre entière responsabilité.

> [!NOTE]
> Vous devez tronquer ou supprimer le fichier journal occasionnellement pour éviter qu’il ne devienne trop volumineux.

 La procédure suivante décrit comment définir un emplacement de fichier journal personnalisé pour un seul client.

### <a name="to-set-a-custom-log-file-location"></a>Pour définir un emplacement de fichier journal personnalisé

1. Ouvrez **Regedit.exe**.

2. Accédez au nœud `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Définissez la valeur de chaîne `LogFilePath` sur le chemin d’accès complet et le nom de fichier de votre emplacement de journal personnalisé préféré.

     Cet emplacement doit se trouver dans un répertoire auquel l’utilisateur a accès en écriture. Par exemple, sur Windows Vista, créez la structure de dossiers suivante et affectez-lui la valeur `LogFilePath` *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Voir aussi
- [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)