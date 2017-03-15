---
title: "Comment&#160;: v&#233;rifier les param&#232;tres des propri&#233;t&#233;s IIS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer les applications Web, dépanner"
  - "IIS (outil d'administration)"
  - "IIS, paramètres des propriétés"
  - "propriétés (débogueur), définir à l'aide de l'outil d'administration IIS"
  - "applications Web, définir des propriétés"
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Comment&#160;: v&#233;rifier les param&#232;tres des propri&#233;t&#233;s IIS
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez définir les propriétés d'une application Web à l'aide de l'outil d'administration IIS.  Ces propriétés doivent être correctement définies pour que l'application s'exécute. Il est donc souvent nécessaire de vérifier ces paramètres pour pouvoir dépanner.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour vérifier les paramètres IIS pour l'application Web  
  
1.  Ouvrez la fenêtre **Outils d'administration** : Dans le menu **Démarrer**, pointez sur **Programmes**, puis cliquez sur **Outils d'administration**.  Si **Outils d'administration** n'apparaît pas dans le menu **Programmes**, recherchez\-le dans le **Panneau de configuration**.  
  
    -   Sous Windows 2000, sélectionnez **Gestionnaire des services Internet**.  
  
    -   Sous Windows XP, sélectionnez **Services IIS \(Internet Information Services\)**.  
  
    -   Sous Windows Server 2003, double\-cliquez sur **Gérer votre serveur**.  
  
         La fenêtre **Gérer votre serveur** s'ouvre.  Sous **Serveur d'applications**, cliquez sur **Gérer ce serveur d'applications**.  
  
         La fenêtre **Serveur d'applications** s'ouvre.  Ouvrez le nœud **Gestionnaire des services Internet \(IIS\)** dans le volet gauche.  
  
2.  Dans la boîte de dialogue, cliquez sur le nœud du contrôle d'arborescence de votre ordinateur.  Cliquez sur le nœud **Sites Web** et sélectionnez le nœud de l'application Web.  Ce sera soit un nœud site Web, et donc un frère du nœud **Site Web par défaut**, ou un nœud de répertoire virtuel sous un nœud de site Web existant.  
  
3.  Cliquez avec le bouton droit sur l'application Web, et dans le menu contextuel, cliquez sur **Propriétés**.  
  
4.  Vérifiez les paramètres de sécurité de l'application Web :  
  
    1.  Dans la fenêtre **Propriétés** de l'application Web, cliquez sur l'onglet **Sécurité du répertoire**, puis sur **Modifier**.  
  
    2.  Dans la boîte de dialogue **Méthodes d'authentification**, sélectionnez **Activer la connexion anonyme** et **Authentification intégrée Windows** si elles ne sont pas déjà sélectionnées.  
  
    3.  Cliquez sur **OK** pour fermer la boîte de dialogue **Méthodes d'authentification**.  
  
5.  Pour une application ATL Server, vérifiez que le verbe DEBUG est associé à votre extension ISAPI.  Pour plus d'informations, consultez [How to: Associate DEBUG Verb with Extension](http://msdn.microsoft.com/fr-fr/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Pour une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], assurez\-vous que le dossier virtuel de l'application comporte un nom d'application défini dans le **Gestionnaire des services Internet \(IIS\)**, le **Gestionnaire des services Internet** ou dans les **Services IIS \(Internet Information Services\)**.  
  
    1.  Dans la fenêtre **Propriétés** de l'application Web, sélectionnez l'onglet **Répertoire**, si l'application est dans un répertoire virtuel, ou l'onglet **Répertoire de base**, si l'application se trouve sur un site Web.  
  
    2.  Vérifiez que le nom dans le **Chemin local** correspond au nom du répertoire où l'application a réellement été déployée.  
  
    3.  Sous **Paramètres d'application**, tapez le nom du répertoire racine qui contient l'application.  
  
    4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.  
  
7.  Pour une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], cliquez sur l'onglet **ASP.NET** et vérifiez que la version correcte de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] est spécifiée.  
  
8.  Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue **Gestionnaire des services Internet \(IIS\)**, **Gestionnaire des services Internet**ou **Services Internet \(IIS\)**.  
  
## Voir aussi  
 [Dépannage](../debugger/debugging-web-applications-troubleshooting.md)