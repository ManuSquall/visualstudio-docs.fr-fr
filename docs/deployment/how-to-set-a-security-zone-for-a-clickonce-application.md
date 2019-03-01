---
title: 'Comment : définir une Zone de sécurité pour une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcb89fea3e364c5933a4b1cfeaf90b44dc14e83d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606835"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Guide pratique pour définir une zone de sécurité pour une application ClickOnce
Quand vous définissez des autorisations de sécurité d’accès du code pour une application ClickOnce, vous devez d’abord définir un ensemble d’autorisations de base dans la page **Sécurité** du **Concepteur de projet**.

 Dans la plupart des cas, vous pouvez aussi sélectionner la zone **Internet** qui contient un ensemble limité d’autorisations, ou la zone **Intranet local** qui fournit un ensemble plus complet d’autorisations. Si votre application nécessite des autorisations personnalisées, sélectionnez la zone de sécurité **Personnalisée** pour les définir. Pour plus d’informations sur la définition d’autorisations personnalisées, consultez [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Pour définir une zone de sécurité

1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2.  Cliquez sur l'onglet **Sécurité** .

3.  Cochez la case **Activer les paramètres de sécurité ClickOnce** .

4.  Sélectionnez la case d’option **Il s’agit d’une application de confiance partielle** .

     Les contrôles de la section **Autorisations de sécurité ClickOnce** sont activés.

5.  Dans la liste déroulante **Zone à partir de laquelle votre application sera installée** , sélectionnez une zone de sécurité.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
