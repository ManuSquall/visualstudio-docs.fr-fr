---
title: 'Erreur : Le débogage a échoué car l’authentification Windows intégrée n’est pas activée. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 074c6c1cace31797e46a192ec0891f1e13dac22b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684272"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Erreur : le débogage a échoué, car l’authentification Windows intégrée n’est pas activée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'authentification de l'utilisateur qui a demandé le débogage a été empêchée en raison d'une erreur d'authentification. Cette erreur peut se produire lorsque vous essayez d’accéder à une application web ou à un service web XML. Cette erreur peut provenir, par exemple, du fait que l'authentification Windows intégrée n'est pas activée. Pour l'activer, suivez les étapes décrites dans Activer l'authentification Windows intégrée.  
  
 Si vous avez activé l’authentification Windows intégrée et que cette erreur persiste, il est possible que celle-ci soit provoquée par l’activation de l’option **Authentification Digest pour les serveurs de domaine Windows**. Dans ce cas, contactez votre administrateur réseau.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Pour activer l'authentification intégrée Windows  
  
1. Ouvrez une session sur le serveur web à l’aide d’un compte d’administrateur.  
  
2. Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.  
  
3. Dans le **Panneau de configuration**, double-cliquez sur **Outils d’administration**.  
  
4. Double-cliquez sur **Services IIS**.  
  
5. Cliquez sur le nœud du serveur web.  
  
     Un dossier **Sites web** s’ouvre sous le nom du serveur.  
  
6. Vous pouvez configurer l’authentification pour tous les sites web ou pour certains sites web. Pour configurer l’authentification pour tous les sites web, cliquez avec le bouton droit sur le dossier **Sites web**, puis cliquez sur **Propriétés**. Pour configurer l’authentification pour un site web individuel, ouvrez le dossier **Sites web**, cliquez avec le bouton droit sur le site web individuel, puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Propriétés** s’affiche.  
  
7. Cliquez sur l’onglet **Sécurité de répertoire**.  
  
8. Dans la section **Connexions anonymes et contrôle d’authentification**, cliquez sur le bouton **Modifier**.  
  
     La boîte de dialogue **Méthodes d’authentification** s’affiche.  
  
9. Sous **Accès authentifié**, sélectionnez **Authentification Windows intégrée**.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue **Méthodes d’authentification**.  
  
11. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.  
  
12. Fermez la fenêtre **Services IIS**.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Pour activer l'authentification Windows intégrée dans Windows Vista/IIS 7  
  
1. Ouvrez une session sur le serveur web à l’aide d’un compte d’administrateur.  
  
2. Activez l'authentification Windows et la compatibilité avec la gestion IIS 6, si ce n'est déjà fait, en procédant comme suit :  
  
    1. Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration** puis cliquez sur **programmes**.  
  
    2. Sous **Programmes et fonctionnalités**, cliquez sur **Activer ou désactiver des fonctionnalités Windows**.  
  
         La boîte de dialogue Contrôle d'accès utilisateur s'affiche et vous invite à confirmer que vous êtes autorisé à poursuivre.  
  
    3. Cliquez sur **Continuer**.  
  
         La boîte de dialogue Fonctionnalités Windows apparaît.  
  
    4. Dans la liste des fonctionnalités, développez le nœud **Services IIS**.  
  
    5. Sous **Services IIS**, développez le nœud **Services World Wide Web**.  
  
    6. Sous **Services World Wide Web**, cliquez sur **Sécurité**.  
  
    7. Cliquez sur **Authentification Windows**.  
  
    8. Sous **Services IIS**, développez le nœud **Outils d’administration web**.  
  
    9. Sous **Outils d’administration web**, développez le nœud **Compatibilité avec la gestion IIS 6** et cochez la case **Compatibilité avec la métabase IIS 6 et la configuration IIS 6**.  
  
    10. Sous **Outils d’administration web**, sélectionnez **Console de gestion IIS**, puis cliquez sur **OK**.  
  
    11. Redémarrez l'ordinateur pour que ces modifications soient prises en compte.  
  
3. Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.  
  
4. Cliquez sur **Affichage classique**, puis double-cliquez sur **Outils d’administration**.  
  
5. Dans la colonne **Nom**, double-cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
6. Dans la colonne **Connexions**, développez le nœud correspondant à votre serveur.  
  
     Un dossier **Sites web** s’ouvre sous le nom du serveur.  
  
7. Développez le nœud **Sites web**, puis cliquez sur le site web pour lequel vous voulez activer l’authentification Windows intégrée.  
  
8. L'intitulé du volet central est remplacé par le nom du site Web sélectionné. Dans ce volet, sous l’en-tête **IIS**, double-cliquez sur **Authentification**.  
  
     L’intitulé du volet est remplacé par **Authentification**.  
  
9. Dans la colonne le volet **Authentification**, dans la colonne **Nom**, cliquez avec le bouton droit sur **Authentification Windows**, puis cliquez sur **Activer**.  
  
10. Fermez la fenêtre **Gestionnaire des services Internet (IIS)**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : Erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft Digest Authentication](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Exécution d’Applications Web sur Vista Windows avec IIS 7.0 et Visual Studio](https://msdn.microsoft.com/library/262a82ac-dd0e-4096-86c6-fb463e88be66)
