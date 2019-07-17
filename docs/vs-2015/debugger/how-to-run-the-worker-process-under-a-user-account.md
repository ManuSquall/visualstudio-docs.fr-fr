---
title: 'Procédure : Exécuter le processus de travail sous un compte d’utilisateur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebb8ec1fe10f6fbc5c367cb0ed127e048351b0e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157868"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Procédure : exécuter le processus Worker sous un compte d’utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour configurer votre ordinateur afin de pouvoir exécuter le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] (aspnet_wp.exe ou w3wp.exe) sous un compte d'utilisateur, procédez comme suit.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Exécuter aspnet_wp.exe sous un compte d'utilisateur  
  
1. Ouvrez le fichier machine.config, situé sur votre ordinateur dans le dossier CONFIG sous le chemin d'accès où vous avez installé le runtime.  
  
2. Recherchez la section &lt;processModel&gt; et remplacez les attributs user et password par le nom et le mot de passe du compte d’utilisateur sous lequel aspnet_wp.exe doit s’exécuter.  
  
3. Enregistrez le fichier machine.config.  
  
4. Sur [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], IIS 6.0 est installé par défaut. Le processus de traitement correspondant est w3wp.exe. Pour fonctionner en mode IIS 6.0 avec aspnet_wp.exe comme processus de traitement, procédez selon les étapes suivantes :  
  
    1. Cliquez sur **Démarrer**, puis sur **Outils d'administration** et choisissez **Services Internet (IIS)** .  
  
    2. Dans la boîte de dialogue **Services Internet** , cliquez avec le bouton droit sur le dossier **Sites Web** et choisissez **Propriétés**.  
  
    3. Dans la boîte de dialogue **Propriétés des sites Web** , choisissez **Service**.  
  
    4. Sélectionnez **Exécuter les services Web en mode d'isolement IIS 6.0**.  
  
    5. Fermez la boîte de dialogue **Propriétés** et **Gestionnaire des services Internet**.  
  
5. Ouvrez une invite de commandes Windows et réinitialisez le serveur en exécutant :  
  
    ```  
    iisreset  
    ```  

    — ou —  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6. Recherchez le dossier des fichiers [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] temporaires, qui doit se trouver sur le même chemin d'accès que le dossier CONFIG. Cliquez avec le bouton droit sur le dossier des fichiers [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] temporaires et sélectionnez **Propriétés** dans le menu contextuel.  
  
7. Dans la boîte de dialogue **Propriétés des fichiers ASP.NET temporaires** , cliquez sur l'onglet **Sécurité** .  
  
8. Cliquez sur **Avancé**.  
  
9. Dans la boîte de dialogue **Paramètres de sécurité avancés des fichiers ASP.NET temporaires** , cliquez sur **Ajouter**.  
  
    La boîte de dialogue **Sélectionner un utilisateur, des ordinateurs ou des groupes** s'affiche.  
  
10. Tapez le nom d'utilisateur dans la zone **Entrez le nom de l'objet à sélectionner** , puis cliquez sur **OK**. Le nom d’utilisateur doit respecter le format : Nomdomaine\nomutilisateur.  
  
11. Dans la boîte de dialogue **Entrée d'autorisation pour les fichiers ASP.Net temporaires** , accordez à l'utilisateur le **Contrôle total**, puis cliquez sur **OK** pour fermer la boîte de dialogue **Entrées des fichiers ASP.Net temporaires** .  
  
12. Une boîte de dialogue **Sécurité** apparaît, vous demandant si vous souhaitez réellement modifier les autorisations pour un dossier système. Cliquez sur **Oui**.  
  
13. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés des fichiers ASP.Net temporaires** .  
  
## <a name="see-also"></a>Voir aussi  
[Débogage ASP.NET : configuration système requise](../debugger/aspnet-debugging-system-requirements.md)  
