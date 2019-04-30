---
title: 'Procédure : Vérifiez les paramètres des propriétés IIS | Microsoft Docs'
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
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ab2b6981094ffbdfcd6544198179924b4e1c53a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444782"
---
# <a name="how-to-verify-iis-property-settings"></a>Procédure : Vérifier les paramètres des propriétés IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir les propriétés d'une application Web à l'aide de l'outil d'administration IIS. Ces propriétés doivent être correctement définies pour que l'application s'exécute. Il est donc souvent nécessaire de vérifier ces paramètres pour pouvoir dépanner.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Pour vérifier les paramètres IIS pour l'application Web  
  
1. Ouvrez le **outils d’administration** fenêtre : Sur le **Démarrer** menu, pointez sur **programmes**, puis cliquez sur **outils d’administration**. Si **Outils d’administration** n’apparaît pas dans le menu **Programmes**, recherchez-le dans le **Panneau de configuration**.  
  
    - Sur Windows 2000, sélectionnez **Gestionnaire des services Internet**.  
  
    - Sur Windows XP, sélectionnez **Services IIS (Internet Information Services)**.  
  
    - Sur Windows Server 2003, double-cliquez sur **Gérer votre serveur**.  
  
         La fenêtre **Gérer votre serveur** s’ouvre. Sous **Serveur d’applications**, cliquez sur **Gérer ce serveur d’applications**.  
  
         La fenêtre **Serveur d’applications** s’ouvre. Ouvrez le nœud **Gestionnaire des services Internet (IIS)** dans le volet gauche.  
  
2. Dans la boîte de dialogue, cliquez sur le nœud du contrôle d’arborescence de votre ordinateur. Cliquez sur le nœud **Sites web** et sélectionnez le nœud de l’application web. Ce sera soit un nœud de site web, et donc un frère du nœud **Site web par défaut**, ou un nœud de répertoire virtuel sous un nœud de site web existant.  
  
3. Cliquez avec le bouton droit sur l’application web et, dans le menu contextuel, cliquez sur **Propriétés**.  
  
4. Vérifiez les paramètres de sécurité de l'application Web :  
  
    1. Dans la fenêtre **Propriétés** de l’application web, cliquez sur l’onglet **Sécurité du répertoire**, puis sur **Modifier**.  
  
    2. Dans la boîte de dialogue **Méthodes d’authentification**, sélectionnez **Activer la connexion anonyme** et **Authentification Windows intégrée** si elles ne sont pas déjà sélectionnées.  
  
    3. Cliquez sur **OK** pour fermer la boîte de dialogue **Méthodes d’authentification**.  
  
5. Pour une application ATL Server, vérifiez que le verbe DEBUG est associé à votre extension ISAPI. Pour plus d'informations, voir [Procédure : Associer le verbe DEBUG avec l’Extension](http://msdn.microsoft.com/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6. Pour une application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], vérifiez que le dossier virtuel de l’application comporte un nom d’application défini dans le **Gestionnaire des services Internet (IIS)**, le **Gestionnaire des services Internet** ou les **Services IIS (Internet Information Services)**.  
  
    1. Dans la fenêtre **Propriétés** de l’application web, sélectionnez l’onglet **Répertoire** si l’application est dans un répertoire virtuel, ou l’onglet **Répertoire de base** si l’application se trouve sur un site web.  
  
    2. Vérifiez que le nom dans le **Chemin local** correspond au nom du répertoire où l’application a été réellement déployée.  
  
    3. Sous **Paramètres d’application**, tapez le nom du répertoire racine qui contient l’application.  
  
    4. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.  
  
7. Pour une application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], cliquez sur l’onglet **ASP.NET** et vérifiez que la version correcte de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] est spécifiée.  
  
8. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue **Gestionnaire des services Internet (IIS)**, **Gestionnaire des services Internet** ou **Services Internet (IIS)**.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes](../debugger/debugging-web-applications-troubleshooting.md)
