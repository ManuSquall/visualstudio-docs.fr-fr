---
redirect_url: /visualstudio/ide/microsoft-help-viewer
ms.openlocfilehash: c0b1a114eb157860dd70873929727cc56f1d6514
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
title: "Résolution des problèmes liés à Help Viewer | Microsoft Docs" ms.custom: "" ms.date: "11/04/2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "résolution des problèmes [Help Viewer]"
  - "Help Viewer, résolution des problèmes" ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12 caps.latest.revision: 13 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="troubleshooting-the-help-viewer"></a>Résolution des problèmes liés à Help Viewer
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
  
-   Pour plus d’informations, consultez le forum [Developer Documentation and Help System](http://go.microsoft.com/fwlink/?LinkId=232741).  
  
## <a name="see-also"></a>Voir aussi
[Guide de l’administrateur Help Viewer](http://go.microsoft.com/fwlink/?LinkId=243985)