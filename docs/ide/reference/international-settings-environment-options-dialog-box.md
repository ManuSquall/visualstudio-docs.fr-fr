---
title: Paramètres internationaux, Environnement, boîte de dialogue Options
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74a0380cd7d31f0c7a3e8d94a9232efa908ee89f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833138"
---
# <a name="international-settings-environment-options-dialog-box"></a>Paramètres internationaux, Environnement, boîte de dialogue Options

La page Paramètres internationaux vous permet de changer la langue par défaut quand vous avez plusieurs versions linguistiques de l'environnement de développement intégré (IDE) installé sur votre ordinateur. Vous pouvez accéder à cette boîte de dialogue en sélectionnant **Options** dans le menu **Outils**, puis en choisissant **Paramètres internationaux** dans le dossier **Environnement**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

**Language**

Répertorie les langues disponibles pour les versions linguistiques du produit installé. Cette option n'est disponible que si vous avez plusieurs versions linguistiques installées sur votre ordinateur. Si plusieurs versions linguistiques de produits ou si une installation mixte de versions linguistiques de produits partagent le même environnement, la langue sélectionnée est changée en **Identique à Microsoft Windows**.

> [!CAUTION]
> Dans un système où plusieurs langues sont installées, les outils de génération Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe et les fichiers associés) ne sont pas affectés par ce paramètre. Ces outils utilisent la version pour la dernière langue installée. Les outils de génération pour la langue précédemment installée sont remplacés, car Visual C++ Build Tools n’utilise pas le modèle de DLL satellite.

## <a name="see-also"></a>Voir aussi

- [Installer des modules linguistiques](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)