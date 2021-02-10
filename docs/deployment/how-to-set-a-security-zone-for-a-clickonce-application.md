---
title: Définir la zone de sécurité (application ClickOnce)
description: En savoir plus sur la définition des autorisations de sécurité d’accès du code pour une application ClickOnce, qui commence par un jeu d’autorisations de base dans le concepteur de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23174667827e63afb93d82679a51d65512731710
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946070"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Guide pratique pour définir une zone de sécurité pour une application ClickOnce
Quand vous définissez des autorisations de sécurité d’accès du code pour une application ClickOnce, vous devez d’abord définir un ensemble d’autorisations de base dans la page **Sécurité** du **Concepteur de projet**.

 Dans la plupart des cas, vous pouvez aussi sélectionner la zone **Internet** qui contient un ensemble limité d’autorisations, ou la zone **Intranet local** qui fournit un ensemble plus complet d’autorisations. Si votre application nécessite des autorisations personnalisées, sélectionnez la zone de sécurité **Personnalisée** pour les définir. Pour plus d’informations sur la définition d’autorisations personnalisées, consultez [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Pour définir une zone de sécurité

1. Quand un projet est sélectionné dans **Explorateur de solutions**, dans le menu **projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Security** .

3. Cochez la case **Activer les paramètres de sécurité ClickOnce** .

4. Sélectionnez la case d’option **Il s’agit d’une application de confiance partielle** .

     Les contrôles de la section **Autorisations de sécurité ClickOnce** sont activés.

5. Dans la liste déroulante **Zone à partir de laquelle votre application sera installée** , sélectionnez une zone de sécurité.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
