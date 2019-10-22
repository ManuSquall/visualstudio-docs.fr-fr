---
title: Résolution des problèmes de la visionneuse d’aide | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 490525cded11a4cddbbfb3f650d87c55b2fa196b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654771"
---
# <a name="troubleshooting-the-help-viewer"></a>Résolution des problèmes liés à la Visionneuse d'aide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique traite des problèmes que vous pouvez rencontrer avec Help Viewer.

## <a name="audio-doesnt-work"></a>L’audio ne fonctionne pas.
 Help Viewer n’a pas de lecteur audio intégré. Si vous avez téléchargé du contenu audio et que rien ne se passe lorsque vous cliquez sur **Lire**, installez un lecteur audio.

## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>La recherche ne fonctionne pas dans Windows Server 2008, Windows Server 2008 avec SP1 et Windows Server 2008 R2.
 Les fonctionnalités de recherche et de filtre de Help Viewer nécessitent l’installation et l’activation du service Windows Search. Par défaut, ce service est désactivé dans Windows Server 2008, Windows Server 2008 avec Service Pack 1 (SP1) et Windows Server 2008 R2.

#### <a name="to-activate-windows-search-service"></a>Pour activer le service Windows Search

1. Démarrez le Gestionnaire de serveur.

2. Dans le volet de navigation de gauche, choisissez **Rôles**.

3. Dans le volet Résumé des rôles, choisissez **Ajouter le rôle**.

4. Choisissez le rôle Services de fichiers, puis cliquez sur le bouton **Suivant**.

5. Choisissez le service de rôle Windows Search.

## <a name="additional-resources"></a>Ressources supplémentaires
 Vous pouvez obtenir plus d’informations sur Help Viewer et envoyer vos commentaires à son sujet en utilisant les ressources suivantes :

- Pour envoyer vos commentaires, accédez à [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) sur le site web Microsoft ou envoyez un e-mail à [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).

- Pour plus d’informations, consultez la documentation du développeur et le Forum du [système d’aide](http://go.microsoft.com/fwlink/?LinkId=232741) et le blog de [l’aide](http://go.microsoft.com/fwlink/?LinkId=232743) .

## <a name="see-also"></a>Voir aussi
 [Guide de l’administrateur Help Viewer 2.1](http://go.microsoft.com/fwlink/?LinkId=243985)
