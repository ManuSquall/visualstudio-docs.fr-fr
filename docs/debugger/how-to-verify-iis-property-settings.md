---
title: 'Procédure : Vérifiez les paramètres des propriétés IIS | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5941dec4b21e044873a2ae95ae7682867b4bd67
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037016"
---
# <a name="how-to-verify-iis-property-settings"></a>Procédure : Vérifier les paramètres des propriétés IIS

Vous pouvez définir les propriétés d'une application Web à l'aide de l'outil d'administration IIS. Ces propriétés doivent être correctement définies pour que l'application s'exécute. Il est donc souvent nécessaire de vérifier ces paramètres pour pouvoir dépanner.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Pour vérifier les paramètres IIS pour l'application Web

1. Ouvrez la fenêtre **Outils d’administration**. Sur le **Démarrer** menu, pointez sur **programmes**, puis cliquez sur **outils d’administration**. Si **Outils d’administration** n’apparaît pas dans le menu **Programmes**, recherchez-le dans le **Panneau de configuration**.

   -   Sur Windows 2000, sélectionnez **Gestionnaire des services Internet**.

   -   Sur Windows XP, sélectionnez **Services IIS (Internet Information Services)**.

   -   Sur Windows Server 2003, double-cliquez sur **Gérer votre serveur**.

        La fenêtre **Gérer votre serveur** s’ouvre. Sous **Serveur d’applications**, cliquez sur **Gérer ce serveur d’applications**.

        La fenêtre **Serveur d’applications** s’ouvre. Ouvrez le nœud **Gestionnaire des services Internet (IIS)** dans le volet gauche.

2. Dans la boîte de dialogue, cliquez sur le nœud du contrôle d’arborescence de votre ordinateur. Cliquez sur le nœud **Sites web** et sélectionnez le nœud de l’application web. Ce sera soit un nœud de site web, et donc un frère du nœud **Site web par défaut**, ou un nœud de répertoire virtuel sous un nœud de site web existant.

3. Cliquez avec le bouton droit sur l’application web et, dans le menu contextuel, cliquez sur **Propriétés**.

4. Vérifiez les paramètres de sécurité de l'application Web :

   1.  Dans la fenêtre **Propriétés** de l’application web, cliquez sur l’onglet **Sécurité du répertoire**, puis sur **Modifier**.

   2.  Dans la boîte de dialogue **Méthodes d’authentification**, sélectionnez **Activer la connexion anonyme** et **Authentification Windows intégrée** si elles ne sont pas déjà sélectionnées.

   3.  Cliquez sur **OK** pour fermer la boîte de dialogue **Méthodes d’authentification**.

5. Pour une application ATL Server, vérifiez que le verbe DEBUG est associé à votre extension ISAPI. Pour plus d'informations, voir [Procédure : Associer le verbe DEBUG avec l’Extension](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e).

6. Pour une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vérifiez que le dossier virtuel de l’application comporte un nom d’application défini dans le **Gestionnaire des services Internet (IIS)**, le **Gestionnaire des services Internet** ou les **Services IIS (Internet Information Services)**.

   1.  Dans la fenêtre **Propriétés** de l’application web, sélectionnez l’onglet **Répertoire** si l’application est dans un répertoire virtuel, ou l’onglet **Répertoire de base** si l’application se trouve sur un site web.

   2.  Vérifiez que le nom dans le **Chemin local** correspond au nom du répertoire où l’application a été réellement déployée.

   3.  Sous **Paramètres d’application**, tapez le nom du répertoire racine qui contient l’application.

   4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.

7. Pour une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], cliquez sur l’onglet **ASP.NET** et vérifiez que la version correcte de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] est spécifiée.

8. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.

9. Cliquez sur **OK** pour fermer la boîte de dialogue **Gestionnaire des services Internet (IIS)**, **Gestionnaire des services Internet** ou **Services Internet (IIS)**.

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes](../debugger/debugging-web-applications-troubleshooting.md)