---
title: Paramètres de sécurité avancés, boîte de dialogue
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d34d1b16f36c90f4200a091050d1646fc563d33
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419079"
---
# <a name="advanced-security-settings-dialog-box"></a>Paramètres de sécurité avancés, boîte de dialogue

Cette boîte de dialogue vous permet de spécifier les paramètres de sécurité concernant le débogage dans la zone.

![Boîte de dialogue Paramètres de sécurité avancés dans Visual Studio](../media/advanced-security-settings.png)

Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projets** apparaît, cliquez sur l’onglet **sécurité** . Sur la page **sécurité** , sélectionnez **activer les paramètres de sécurité ClickOnce**, cliquez sur **il s’agit d’une application de confiance partielle**, puis sur **avancé**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

**Autoriser l’application à accéder à son site d’origine**

Si cette case est cochée, l’application peut accéder au site web ou au partage serveur sur lequel il est publié. Cette option est activée par défaut.

**Déboguer cette application comme si elle était téléchargée de l’URL suivante**

Si vous devez permettre à l’application d’accéder au site web ou au partage serveur correspondant à **l’URL d’installation** spécifiée sur la page **Publier**, entrez cette URL ici. Cette option est disponible uniquement quand l’option **Autoriser l’application à accéder à son site d’origine** est sélectionnée.

## <a name="see-also"></a>Voir aussi

- [Page Sécurité, Concepteur de projets](../../ide/reference/security-page-project-designer.md)
