---
title: "Erreur&#160;: le d&#233;bogage a &#233;chou&#233;, car l&#39;authentification int&#233;gr&#233;e de Windows n&#39;est pas activ&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.webdbg_ntlm_authn_not_enabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "débogueur, erreurs d'applications Web"
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: le d&#233;bogage a &#233;chou&#233;, car l&#39;authentification int&#233;gr&#233;e de Windows n&#39;est pas activ&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'authentification de l'utilisateur qui a demandé le débogage a été empêchée en raison d'une erreur d'authentification.  Cette erreur peut se produire lorsque vous essayez d'accéder à une application Web ou à un service Web XML.  Cette erreur peut provenir, par exemple, du fait que l'authentification Windows intégrée n'est pas activée.  Pour l'activer, suivez les étapes décrites dans Activer l'authentification Windows intégrée.  
  
 Si vous avez activé l'authentification Windows intégrée et que cette erreur persiste, il est possible que celle\-ci soit provoquée par l'activation de l'option **Authentification Digest pour les serveurs de domaine Windows**.  Dans ce cas, contactez votre administrateur réseau.  
  
### Pour activer l'authentification intégrée Windows  
  
1.  Ouvrez une session sur le serveur Web à l'aide d'un compte d'administrateur.  
  
2.  Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.  
  
3.  Dans **Panneau de configuration**, double\-cliquez sur **Outils d'administration**.  
  
4.  Double\-cliquez sur **Services Internet \(IIS\)**.  
  
5.  Cliquez sur le nœud du serveur Web.  
  
     Un dossier **Sites Web** s'ouvre sous le nom du serveur.  
  
6.  Vous pouvez configurer l'authentification pour tous les sites Web ou pour certains sites Web.  Pour configurer l'authentification pour tous les sites Web, cliquez avec le bouton droit sur le dossier **Sites Web** et cliquez sur **Propriétés**.  Pour configurer l'authentification pour un site Web individuel, ouvrez le dossier **Sites Web**, cliquez avec le bouton droit sur le site Web individuel, puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Propriétés** s'affiche.  
  
7.  Cliquez sur l'onglet **Sécurité de répertoire**.  
  
8.  Dans la section **Connexions anonymes et contrôle d'authentification**, cliquez sur le bouton **Modifier**.  
  
     La boîte de dialogue **Méthodes d'authentification** s'affiche.  
  
9. Sous **Accès authentifié**, sélectionnez **Authentification Windows intégrée**.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue **Méthodes d'authentification**.  
  
11. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.  
  
12. Fermez la fenêtre **Services Internet \(IIS\)**.  
  
### Pour activer l'authentification Windows intégrée dans Windows Vista\/IIS 7  
  
1.  Ouvrez une session sur le serveur Web à l'aide d'un compte d'administrateur.  
  
2.  Activez l'authentification Windows et la compatibilité avec la gestion IIS 6, si ce n'est déjà fait, en procédant comme suit :  
  
    1.  Cliquez sur **Démarrer**, **Panneau de configuration**, puis **Programmes**.  
  
    2.  Sous **Programmes et fonctionnalités**, cliquez sur **Activer ou désactiver des fonctionnalités Windows**.  
  
         La boîte de dialogue Contrôle d'accès utilisateur s'affiche et vous invite à confirmer que vous êtes autorisé à poursuivre.  
  
    3.  Cliquez sur **Continuer**.  
  
         La boîte de dialogue Fonctionnalités Windows apparaît.  
  
    4.  Dans la liste des fonctionnalités, développez le nœud **Services Internet \(IIS\)**.  
  
    5.  Sous **Services Internet \(IIS\)**, développez le nœud **Services World Wide Web**.  
  
    6.  Sous **Services World Wide Web**, cliquez sur **Sécurité**.  
  
    7.  Cliquez sur **Authentification Windows**.  
  
    8.  Sous **Services Internet \(IIS\)**, développez le nœud **Outils d'administration Web**.  
  
    9. Sous **Outils d'administration Web**, développez le nœud **Compatibilité avec la gestion IIS 6** et activez la case à cocher **Compatibilité avec la métabase IIS et la configuration IIS 6**.  
  
    10. Sous **Outils d'administration Web**, sélectionnez **Console de gestion IIS**, puis cliquez sur **OK**.  
  
    11. Redémarrez l'ordinateur pour que ces modifications soient prises en compte.  
  
3.  Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.  
  
4.  Cliquez sur **Affichage classique**, puis double\-cliquez sur **Outils d'administration**.  
  
5.  Dans la colonne **Nom**, double\-cliquez sur **Gestionnaire des services Internet \(IIS\)**.  
  
6.  Dans la colonne **Connexions**, développez le nœud correspondant à votre serveur.  
  
     Un dossier **Sites Web** s'ouvre sous le nom du serveur.  
  
7.  Développez le nœud **Sites Web**, puis cliquez sur le site Web pour lequel vous voulez activer l'authentification Windows intégrée.  
  
8.  L'intitulé du volet central est remplacé par le nom du site Web sélectionné.  Dans ce volet, sous l'en\-tête **IIS**, double\-cliquez sur **Authentification**.  
  
     L'intitulé du volet est remplacé par **Authentification**.  
  
9. Dans la colonne **Nom** du volet **Authentification**, cliquez avec le bouton droit sur **Authentification Windows**, puis cliquez sur **Activer**.  
  
10. Fermez la fenêtre **Gestionnaire des services Internet \(IIS\)**.  
  
## Voir aussi  
 [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft Digest Authentication](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Running Web Applications on Windows Vista with IIS 7.0 and Visual Studio](../Topic/Running%20Web%20Applications%20on%20Windows%20Vista%20with%20IIS%207.0%20and%20Visual%20Studio.md)