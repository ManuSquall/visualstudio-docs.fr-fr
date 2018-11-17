---
title: 'Erreur : Échec de connexion à distance du groupe de travail | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b13531d3a9dd5249b0c96ddc4e8f736c20696303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723663"
---
# <a name="error-workgroup-remote-logon-failure"></a>Erreur : Échec d'ouverture de session à distance du groupe de travail
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur affiche le message suivant :  
  
 Échec d'ouverture de session : nom d'utilisateur inconnu ou mot de passe incorrect  
  
 **Cause**  
  
 Cette erreur peut se produire lorsque vous déboguez à partir d'un ordinateur au sein d'un groupe de travail et que vous tentez de vous connecter à un ordinateur distant. Plusieurs causes sont possibles :  
  
-   Il n'existe pas de compte avec le nom et le mot de passe correspondants sur l'ordinateur distant.  
  
-   Si l’ordinateur Visual Studio et l’ordinateur distant se trouvent sur des groupes de travail, cette erreur peut se produire en raison de la valeur par défaut **stratégie de sécurité locale** définition sur l’ordinateur distant. Le paramètre par défaut pour le **stratégie de sécurité locale** paramètre est **invité seul - les utilisateurs locaux s’authentifient en tant qu’invité**. Pour déboguer sur cette installation, vous devez modifier le paramètre sur l’ordinateur distant à **classique - les utilisateurs locaux s’authentifient eux-mêmes**.  
  
> [!NOTE]
>  Vous devez être administrateur pour exécuter les tâches suivantes.  
  
### <a name="to-open-the-local-security-policy-window"></a>Pour ouvrir la fenêtre Stratégie de sécurité locale  
  
1.  Démarrer le **secpol.msc** le composant logiciel enfichable Microsoft Management Console. Tapez secpol.msc dans la zone de recherche Windows, dans la zone Exécuter de Windows, ou dans une invite de commandes.  
  
### <a name="to-add-user-rights-assignments"></a>Pour ajouter des assignations de droits utilisateur  
  
1.  Ouvrez les Paramètres régionaux  
  
2.  Ouvrez le **stratégie de sécurité locale** fenêtre.  
  
3.  Développez le **stratégies locales** dossier.  
  
4.  Cliquez sur **attribution des droits utilisateur**.  
  
5.  Dans le **stratégie** colonne, double-cliquez sur **déboguer des programmes** pour afficher les affectations de stratégie de groupe local actuel dans le **paramètre de stratégie de sécurité locale** boîte de dialogue.  
  
     ![Droits d’utilisateur de stratégie de sécurité locale](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Pour ajouter de nouveaux utilisateurs, cliquez sur le **ajouter un utilisateur ou groupe** bouton.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Pour modifier le modèle de partage et de sécurité  
  
1.  Ouvrez le **stratégie de sécurité locale** fenêtre.  
  
2.  Développez le **stratégies locales** dossier.  
  
3.  Cliquez sur **Options de sécurité**.  
  
4.  Dans le **stratégie** colonne, double-cliquez sur **accès réseau : modèle de partage et de sécurité pour les comptes locaux**.  
  
5.  Dans le **accès réseau : modèle de partage et de sécurité pour les comptes locaux** boîte de dialogue, changez la valeur à **classique - les utilisateurs locaux s’authentifient eux-mêmes** et cliquez sur le **appliquer**bouton.  
  
     ![Options de sécurité de stratégie de sécurité locale](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



