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
ms.openlocfilehash: 2cedc9f45d2e21684496bd882de4aa74b3bf8b3d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851080"
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

- Pour envoyer vos commentaires, accédez à [Microsoft Connect](https://connect.microsoft.com/) sur le site web Microsoft ou envoyez un e-mail à [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).

- Pour plus d’informations, consultez la documentation du développeur et le Forum du [système d’aide](https://social.msdn.microsoft.com/Forums/en-US/devdocs/threads) et le blog de [l’aide](https://blogs.msdn.com/b/thehelpguy/) .

## <a name="see-also"></a>Voir aussi
 [Guide de l’administrateur Help Viewer 2.1](https://msdn.microsoft.com/library/hh492077(VS.110).aspx)
