---
title: "Erreur&#160;: impossible de d&#233;marrer le d&#233;bogage sur le serveur Web | Microsoft Docs"
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
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, erreurs d'applications Web"
  - "déboguer (Visual Studio), erreurs"
  - "déboguer les applications Web ASP.NET, erreur : impossible de démarrer le débogage"
  - "erreurs (débogueur), impossible de démarrer le débogage"
  - "serveurs HTTP, erreur de débogage"
  - "IIS, déboguer des DLL"
  - "débogage distant, erreurs"
  - "sécurité (débogueur), applications Web"
  - "paramètres de sécurité, vérifier les sites Web par défaut"
  - "erreur : impossible de démarrer le débogage"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: impossible de d&#233;marrer le d&#233;bogage sur le serveur Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quand vous essayez de déboguer une application ASP.NET exécutée sur un serveur web, le message d’erreur suivant peut s’afficher : Impossible de démarrer le débogage sur le serveur web.  
  
 Dans la plupart des cas, cette erreur se produit, car IIS n’est pas configuré correctement.  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> Vérifier qu’IIS est correctement configuré  
 Pour plus d’informations sur le déploiement vers IIS 8 avec une application MVC 5, consultez [Publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Pour plus d’informations sur le déploiement vers IIS 7.5, consultez [Débogage distant ASP.NET sur un ordinateur distant IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> Vérifier que les outils de contrôle à distance Visual Studio sont installés  
 Si vous essayez de déboguer sur un serveur web distant, les outils de contrôle à distance Visual Studio doivent être installés. Pour plus d’informations sur le téléchargement et l’installation des outils de contrôle à distance, consultez [Débogage distant](../debugger/remote-debugging.md).  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> Vérifier qu’ASP.NET est installé  
 **IIS 8**  
  
 Pour IIS 8, vous installez ASP.NET dans le cadre d’IIS.  
  
1.  Dans la vignette **Gestionnaire de serveur**, sélectionnez  **Tableau de bord**, puis cliquez sur **Ajouter des rôles et des fonctionnalités**.  
  
2.  Dans la page **Type d’installation**, sélectionnez **Installation basée sur un rôle ou une fonctionnalité** , puis cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner le serveur de destination**, sélectionnez **Sélectionner un serveur du pool de serveurs**, votre serveur, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner des rôles de serveurs**, sélectionnez **Serveur Web \(IIS\)**, puis cliquez sur **Suivant**.  
  
5.  Dans la page **Sélectionner les fonctionnalités**, cliquez sur **Suivant**.  
  
6.  Dans la page du **rôle de serveur Web \(IIS\)**, cliquez sur **Suivant**.  
  
7.  Dans la page **Sélectionner des services de rôle**, notez les services de rôle présélectionnés qui sont installés par défaut, développez le nœud **Serveur d’applications**, le nœud **.NET Framework 4.5**, puis sélectionnez  **ASP.NET 4.5**. \(Si vous avez installé .NET 3.5, sélectionnez également **ASP.NET 3.5**.\)  
  
8.  Dans la page **Confirmer les sélections d’installation**, cliquez sur **Installer**.  
  
9. Dans la page **Progression de l’installation**, vérifiez que votre installation du rôle de serveur Web \(IIS\) et des services de rôle requis a réussi, puis cliquez sur **Fermer**.  
  
 **IIS 7.5 et versions antérieures**  
  
 Pour IIS 7.5 et versions antérieures : à partir d’une fenêtre d’invite de commandes, exécutez la commande suivante :  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## Résolution des problèmes de base  
 Voici quelques opérations que vous pouvez effectuer pour vérifier que votre application ASP.NET est déployée correctement.  
  
## Afficher la page localhost dans le navigateur  
 Si IIS n’est pas installé correctement, vous devez obtenir des erreurs quand vous tapez `http://localhost` dans un navigateur.  
  
## Afficher la page web dans le navigateur  
 Démarrez un navigateur web et tapez l’URL de la page que vous essayez de déboguer \(par exemple : `http://localhost/MyWebApplication`\). Si IIS n’est pas configuré correctement ou que votre application ASP.NET n’est pas déployée correctement, vous devez recevoir des erreurs qui vous aideront à corriger l’installation d’IIS et le déploiement d’ASP.NET.  
  
## Créer une application ASP.NET de base sur le serveur  
 Essayez de créer une application ASP.NET de base localement sur le serveur et tentez de la déboguer.  
  
## Résoudre les erreurs d’authentification si vous utilisez uniquement l’adresse IP  
 Le débogage d'un serveur Web nécessite l'authentification NTLM. Par défaut, les adresses IP sont supposées faire partie d'Internet et l'authentification NTLM ne s'effectue pas via Internet. Pour résoudre ce problème, vous pouvez spécifier le nom de l’ordinateur distant.  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> Attachement manuel au processus  
 Si vous obtenez toujours un message d’erreur quand vous commencez le débogage, vous pouvez essayer de déboguer votre application en utilisant l’attachement manuel au processus.  
  
-   Démarrez l'application sans débogage. \(Dans le menu **Déboguer**, choisissez **Exécuter sans débogage**.\)  
  
-   Cliquez sur **Déboguer\/Attacher au processus**.  Quand la fenêtre s’affiche, activez **Afficher les processus de tous les utilisateurs**.  
  
-   Recherchez le processus approprié et procédez à l’attachement. Pour les applications ASP.NET antérieures à MVC 5, le processus est w3wp.exe. Pour MVC 5, consultez [Publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
## Voir aussi  
 [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)