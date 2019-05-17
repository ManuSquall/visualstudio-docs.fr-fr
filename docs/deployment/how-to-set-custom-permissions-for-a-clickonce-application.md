---
title: 'Procédure : Définir des autorisations personnalisées pour une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c8a6fd6625726f749afcf20b80f83178a47ab92
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407005"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Procédure : Définir des autorisations personnalisées pour une application ClickOnce
Vous pouvez déployer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui utilise les autorisations par défaut pour la zone Internet ou Intranet local. Vous pouvez également créer une zone personnalisée pour les autorisations spécifiques nécessaires à l’application. Vous pouvez pour cela personnaliser les autorisations de sécurité dans la page **Sécurité** du **Concepteur de projets**.

### <a name="to-customize-a-permission"></a>Pour personnaliser une autorisation

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Sécurité** .

3. Cochez la case **Activer les paramètres de sécurité ClickOnce** .

4. Sélectionnez la case d’option **Il s’agit d’une application de confiance partielle** .

     Les contrôles de la section **Autorisations de sécurité ClickOnce** sont activés.

5. Dans la liste déroulante **Zone à partir de laquelle votre application sera installée** , cliquez sur **(Personnalisé)**.

6. Cliquez sur **Modifier les autorisations XML**.

     Le fichier *app.manifest* s’ouvre dans l’éditeur XML.

7. Avant l’élément `</applicationRequestMinimum>` , ajoutez le code XML pour les autorisations dont votre application a besoin.

    > [!NOTE]
    > Vous pouvez utiliser la méthode `ToXml` d’un jeu d'autorisations pour générer le code XML du manifeste d’application. Par exemple, pour générer le code XML pour le jeu d’autorisations <xref:System.Security.Permissions.EnvironmentPermission> , appelez la méthode <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> .

## <a name="see-also"></a>Voir aussi
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
