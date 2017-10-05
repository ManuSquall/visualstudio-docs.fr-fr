---
title: "Synchroniser vos paramètres dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: 1882e191caa027e7a6e2b52c766135b240b309a1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>Synchroniser vos paramètres dans Visual Studio

Quand vous vous connectez à Visual Studio sur plusieurs ordinateurs en utilisant le même compte de personnalisation, vos paramètres sont synchronisés par défaut sur tous les ordinateurs.

## <a name="synchronized-settings"></a>Paramètres synchronisés

Par défaut, les paramètres suivants sont synchronisés.

- Paramètres de développement (vous devez sélectionner un ensemble de paramètres la première fois que vous exécutez Visual Studio, mais vous pouvez modifier la sélection à tout moment. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).)

- Les options suivantes des pages **Outils &#124; Options** :

    - Paramètres **Thème** et paramètres de mise en majuscules de la barre de menus, dans la page d’options **Environnement**, **Général**

    - Tous les paramètres de la page d’options **Environnement**, **Polices et couleurs**

    - Tous les raccourcis clavier de la page d’options **Environnement**, **Clavier**

    - Tous les paramètres de la page d’options **Environnement, onglets et fenêtres**

    - Tous les paramètres de la page d’options **Environnement**, **Démarrage**

    - Tous les paramètres des pages d’options de l’**éditeur de texte**

    - Tous les paramètres des pages d’options du **concepteur XAML**

- Alias de commande définis par l'utilisateur. Pour plus d’informations sur la façon de définir des alias de commande, consultez [Alias de commandes Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Dispositions des fenêtres définies par l’utilisateur dans la page **Fenêtre &#124; Gérer les dispositions de fenêtres**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Désactiver les paramètres synchronisés sur un ordinateur particulier

Les paramètres synchronisés pour Visual Studio sont activés par défaut. Vous pouvez désactiver les paramètres synchronisés sur un ordinateur en accédant à la page **Outils &#124; Options &#124; Environnement &#124; Paramètres synchronisés**, puis en décochant la case correspondante.  Par exemple, si vous décidez de ne pas synchroniser les paramètres de Visual Studio sur l’ordinateur A, toutes les modifications de paramètres effectuées sur l’ordinateur A n’apparaissent pas sur l’ordinateur B ni sur l’ordinateur C. Les ordinateurs B et C continuent à se synchroniser entre eux, mais pas avec l’ordinateur A.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchroniser les paramètres entre les éditions et les produits de la famille Visual Studio

Les paramètres peuvent être synchronisés entre toutes les éditions de Visual Studio, dont Community Edition. Les paramètres sont également synchronisés entre les produits de la famille Visual Studio. Toutefois, chacun de ces produits de la famille peut avoir ses propres paramètres qui ne sont pas partagés avec Visual Studio. Par exemple, les paramètres spécifiques à un produit sur l’ordinateur A seront partagés avec un autre produit sur l’ordinateur B, mais pas avec Visual Studio sur l’ordinateur A ou B.

## <a name="side-by-side-synchronized-settings"></a>Paramètres synchronisés côte à côte

Dans Visual Studio 15.3 et ultérieur, nous avons arrêté de partager certains paramètres (comme la disposition de la fenêtre Outil) entre différentes installations côte à côte de Visual Studio 2017, en changeant l’emplacement du fichier `CurrentSettings.vssettings` situé dans `%userprofile%\Documents\Visual Studio 2017\Settings` pour le placer désormais dans un dossier propre à l’installation et semblable à ceci : `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings`.

**REMARQUE :** Pour utiliser les nouveaux paramètres propres à l’installation, vous devez procéder à une nouvelle installation. Si vous effectuez une mise à niveau d’une installation existante de Visual Studio 2017 vers la dernière mise à jour, elle utilise l’emplacement partagé existant. Si vous disposez actuellement d’installations côte à côte de Visual Studio 2017 et que vous décidez d’effectuer la mise à niveau en utilisant le nouvel emplacement du fichier de paramètres propres à l’installation, effectuez les étapes suivantes :

1. Après la mise à niveau, utilisez l’Assistant Importation/Exportation de paramètres pour exporter tous les paramètres existants vers un emplacement en dehors du dossier `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx`.
2. Ouvrez l’**invite de commandes développeur pour VS 2017** de l’installation de Visual Studio mise à niveau et exécutez `devenv /resetuserdata` à partir de celle-ci.
3. Lancez Visual Studio et importez les paramètres enregistrés du fichier de paramètres exportés.

## <a name="see-also"></a>Voir aussi

[Personnalisation de l’IDE](../ide/personalizing-the-visual-studio-ide.md)

