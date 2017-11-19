---
title: "Comment : vérifier les paramètres de propriété IIS | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0d58ea851423e9239d8685f89890b5d9e152d53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-verify-iis-property-settings"></a>Comment : vérifier les paramètres des propriétés IIS
Vous pouvez définir les propriétés d'une application Web à l'aide de l'outil d'administration IIS. Ces propriétés doivent être correctement définies pour que l'application s'exécute. Il est donc souvent nécessaire de vérifier ces paramètres pour pouvoir dépanner.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Pour vérifier les paramètres IIS pour l'application Web  
  
1.  Ouvrez le **outils d’administration** fenêtre : sur le **Démarrer** menu, pointez sur **programmes**, puis cliquez sur **outils d’administration**. Si **outils d’administration** n’apparaît pas dans le **programmes** menu, recherchez-le dans le **le panneau de configuration**.  
  
    -   Sur Windows 2000, sélectionnez **Gestionnaire des Services Internet**.  
  
    -   Sous Windows XP, sélectionnez **Internet Information Services**.  
  
    -   Sur Windows Server 2003, double-cliquez sur **gérer votre serveur**.  
  
         Le **gérer votre serveur** fenêtre s’ouvre. Sous **serveur d’applications**, cliquez sur **gérer ce serveur d’applications**.  
  
         Le **serveur d’applications** fenêtre s’ouvre. Ouvrez le **Gestionnaire des Services Internet (IIS)** nœud dans le volet gauche.  
  
2.  Dans la boîte de dialogue, cliquez sur le nœud du contrôle d’arborescence de votre ordinateur. Cliquez sur le **Sites Web** nœud, puis sélectionnez le nœud de l’application Web. Ce sera soit un nœud site Web et donc un frère de la **Site Web par défaut** nœud ou un nœud de répertoire virtuel sous un nœud de site Web existant.  
  
3.  Cliquez sur l’application Web et dans le menu contextuel, cliquez sur **propriétés**.  
  
4.  Vérifiez les paramètres de sécurité de l'application Web :  
  
    1.  Dans l’application Web **propriétés** fenêtre, cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **modifier**.  
  
    2.  Dans le **les méthodes d’authentification** boîte de dialogue, sélectionnez **activer l’accès anonyme** et **l’authentification Windows intégrée** si elles ne sont pas déjà sélectionnées.  
  
    3.  Cliquez sur **OK** pour fermer la **les méthodes d’authentification** boîte de dialogue.  
  
5.  Pour une application ATL Server, vérifiez que le verbe DEBUG est associé à votre extension ISAPI. Pour plus d’informations, consultez [Comment : associer le verbe DEBUG avec l’Extension](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Pour un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application, assurez-vous que le dossier virtuel de l’application comporte un nom d’Application défini **Gestionnaire des Services Internet (IIS)**, **Gestionnaire des Services Internet** ou  **Internet Information Services**.  
  
    1.  Dans l’application Web **propriétés** fenêtre, sélectionnez le **active** sous l’onglet si l’application est dans un répertoire virtuel, ou le **répertoire de base** sous l’onglet si l’application se trouve dans un site Web.  
  
    2.  Vérifiez que le nom dans la **chemin d’accès Local** correspond au nom du répertoire où l’application a réellement été déployée.  
  
    3.  Sous **paramètres de l’Application**, tapez le nom du répertoire racine qui contient l’application.  
  
    4.  Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue.  
  
7.  Pour un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application, cliquez sur le **ASP.NET** onglet et vérifiez que la version correcte de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] est spécifié.  
  
8.  Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue.  
  
9. Cliquez sur **OK** pour fermer la **Gestionnaire des Services Internet (IIS)**, **Gestionnaire des Services Internet**, ou **Internet Information Services**boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes](../debugger/debugging-web-applications-troubleshooting.md)