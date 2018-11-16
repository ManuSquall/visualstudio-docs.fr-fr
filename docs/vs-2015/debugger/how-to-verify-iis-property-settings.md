---
title: 'Comment : vérifier les paramètres de propriété IIS | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4639055fe9320c8fd1bf1b2575bca323642dd17f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742073"
---
# <a name="how-to-verify-iis-property-settings"></a>Comment : vérifier les paramètres des propriétés IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir les propriétés d'une application Web à l'aide de l'outil d'administration IIS. Ces propriétés doivent être correctement définies pour que l'application s'exécute. Il est donc souvent nécessaire de vérifier ces paramètres pour pouvoir dépanner.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Pour vérifier les paramètres IIS pour l'application Web  
  
1.  Ouvrez le **outils d’administration** fenêtre : sur le **Démarrer** menu, pointez sur **programmes**, puis cliquez sur **outils d’administration**. Si **outils d’administration** n’apparaît pas dans le **programmes** menu, puis recherchez-le dans le **le panneau de configuration**.  
  
    -   Sur Windows 2000, sélectionnez **Gestionnaire des Services Internet**.  
  
    -   Sur Windows XP, sélectionnez **Internet Information Services**.  
  
    -   Sur Windows Server 2003, double-cliquez sur **gérer votre serveur**.  
  
         Le **gérer votre serveur** fenêtre s’ouvre. Sous **serveur d’applications**, cliquez sur **gérer ce serveur d’applications**.  
  
         Le **serveur d’applications** fenêtre s’ouvre. Ouvrez le **Internet Information Services (IIS) Manager** nœud dans le volet gauche.  
  
2.  Dans la boîte de dialogue, cliquez sur le nœud du contrôle d’arborescence de votre ordinateur. Cliquez sur le **Sites Web** nœud, puis sélectionnez le nœud de l’application Web. Ce sera soit un nœud de site Web et donc un frère de la **Site Web par défaut** nœud ou un nœud de répertoire virtuel sous un nœud de site Web existant.  
  
3.  Cliquez sur l’application Web, puis dans le menu contextuel, cliquez sur **propriétés**.  
  
4.  Vérifiez les paramètres de sécurité de l'application Web :  
  
    1.  Dans l’application Web **propriétés** fenêtre, cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **modifier**.  
  
    2.  Dans le **méthodes d’authentification** boîte de dialogue, sélectionnez **activer l’accès anonyme** et **l’authentification Windows intégrée** si elles ne sont pas déjà sélectionnées.  
  
    3.  Cliquez sur **OK** pour fermer la **méthodes d’authentification** boîte de dialogue.  
  
5.  Pour une application ATL Server, vérifiez que le verbe DEBUG est associé à votre extension ISAPI. Pour plus d’informations, consultez [Comment : associer le verbe DEBUG avec l’Extension](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Pour un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application, assurez-vous que le dossier virtuel de l’application a un nom d’Application défini **Internet Information Services (IIS) Manager**, **Gestionnaire des Services Internet** ou  **Internet Information Services**.  
  
    1.  Dans l’application Web **propriétés** fenêtre, sélectionnez le **Directory** si l’onglet, l’application est dans un répertoire virtuel, ou le **répertoire de base** onglet, si l’application se trouve dans un site Web.  
  
    2.  Vérifiez que le nom dans la **chemin d’accès Local** correspond au nom du répertoire où l’application a réellement été déployée.  
  
    3.  Sous **paramètres de l’Application**, tapez le nom du répertoire racine qui contient l’application.  
  
    4.  Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue.  
  
7.  Pour un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application, cliquez sur le **ASP.NET** onglet et vérifiez que la version correcte du [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] est spécifié.  
  
8.  Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue.  
  
9. Cliquez sur **OK** pour fermer la **Internet Information Services (IIS) Manager**, **Gestionnaire des Services Internet**, ou **Internet Information Services**boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes](../debugger/debugging-web-applications-troubleshooting.md)



