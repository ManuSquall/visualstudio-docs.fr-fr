---
title: Résolution des problèmes de la visionneuse d’aide | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 29c7ee223bbfbeb2dd7b262c33d6c00ea3c41411
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245542"
---
# <a name="troubleshooting-the-help-viewer"></a>Résolution des problèmes liés à la Visionneuse d'aide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique traite des problèmes que vous pouvez rencontrer avec Help Viewer.  
  
## <a name="audio-doesnt-work"></a>L’audio ne fonctionne pas.  
 Help Viewer n’a pas de lecteur audio intégré. Si vous avez téléchargé du contenu audio et que rien ne se passe lorsque vous cliquez sur **Lire**, installez un lecteur audio.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>La recherche ne fonctionne pas dans Windows Server 2008, Windows Server 2008 avec SP1 et Windows Server 2008 R2.  
 Les fonctionnalités de recherche et de filtre de Help Viewer nécessitent l’installation et l’activation du service Windows Search. Par défaut, ce service est désactivé dans Windows Server 2008, Windows Server 2008 avec Service Pack 1 (SP1) et Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Pour activer le service Windows Search  
  
1.  Démarrez le Gestionnaire de serveur.  
  
2.  Dans le volet de navigation de gauche, choisissez **Rôles**.  
  
3.  Dans le volet Résumé des rôles, choisissez **Ajouter le rôle**.  
  
4.  Choisissez le rôle Services de fichiers, puis cliquez sur le bouton **Suivant**.  
  
5.  Choisissez le service de rôle Windows Search.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Vous pouvez obtenir plus d’informations sur Help Viewer et envoyer vos commentaires à son sujet en utilisant les ressources suivantes :  
  
-   Pour envoyer vos commentaires, accédez à [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) sur le site web Microsoft ou envoyez un e-mail à [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Pour plus d’informations, consultez le [Developer Documentation and Help System](http://go.microsoft.com/fwlink/?LinkId=232741) forum et [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) blog.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide Help Viewer 2.1 administrateur](http://go.microsoft.com/fwlink/?LinkId=243985)



