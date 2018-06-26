---
title: Synchroniser vos paramètres
ms.date: 01/23/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 633767e66a4b3d976999574c885a3e6f7a06ddcf
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766127"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchroniser les paramètres Visual Studio sur plusieurs ordinateurs

Quand vous vous connectez à Visual Studio sur plusieurs ordinateurs en utilisant le même compte de personnalisation, vos paramètres peuvent être synchronisés entre les ordinateurs.

## <a name="synchronized-settings"></a>Paramètres synchronisés

Par défaut, les paramètres suivants sont synchronisés :

- Paramètres de développement. Vous devez sélectionner un ensemble de paramètres la première fois que vous exécutez Visual Studio, mais vous pouvez changer la sélection à tout moment. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

- Alias de commande définis par l'utilisateur. Pour plus d’informations sur la façon de définir des alias de commande, consultez [Alias de commandes Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Dispositions de fenêtres définies par l’utilisateur dans la page **Fenêtre** > **Gérer les dispositions de fenêtres**.

- Les options suivantes des pages **Outils** > **Options** :

   - Paramètres de thème et de mise en majuscules de la barre de menus, dans la page d’options **Environnement** > **Général**

   - Tous les paramètres de la page d’options **Environnement** > **Polices et couleurs**

   - Tous les raccourcis clavier de la page d’options **Environnement** > **Clavier**

   - Tous les paramètres de la page d’options **Environnement** > **Onglets et fenêtre**

   - Tous les paramètres de la page d’options **Environnement** > **Démarrage**

   - Tous les paramètres des pages d’options de l’**Éditeur de texte**

   - Tous les paramètres des pages d’options du **Concepteur XAML**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Désactiver les paramètres synchronisés sur un ordinateur particulier

Les paramètres synchronisés pour Visual Studio sont activés par défaut. Vous pouvez désactiver les paramètres synchronisés sur un ordinateur en accédant à la page **Outils** > **Options** > **Environnement** > **Comptes**, et en décochant la case **Synchroniser les paramètres entre les appareils quand ils sont connectés à Visual Studio**. Par exemple, si vous décidez de ne pas synchroniser les paramètres de Visual Studio sur l’ordinateur « A », les changements apportés aux paramètres sur l’ordinateur « A » n’apparaissent pas sur l’ordinateur « B » ou « C ». Les ordinateurs « B » et « C » continuent à se synchroniser entre eux, mais pas avec l’ordinateur « A ».

## <a name="reset-settings"></a>Réinitialiser les paramètres

Vous pouvez réinitialiser tous les paramètres selon une collection de paramètres par défaut en effectuant les étapes suivantes :

1. Dans Visual Studio, sélectionnez **Outils** > **Importation et exportation de paramètres** pour ouvrir l’Assistant **Importation et exportation de paramètres**.

1. Dans l’Assistant **Importation et exportation de paramètres**, sélectionnez **Réinitialiser tous les paramètres**, puis **Suivant**.

   ![Assistant Importation et exportation de paramètres dans Visual Studio](media/reset-all-settings.png)

1. Dans la page **Enregistrer les paramètres actuels**, sélectionnez **Oui** ou **Non**, puis **Suivant**.

1. Dans la page **Choisir une collection de paramètres par défaut**, choisissez une collection, puis sélectionnez **Terminer**.

   ![Collections de paramètres dans Visual Studio](media/settings-collections.png)

1. Dans la page **Réinitialisation terminée**, sélectionnez **Fermer**.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchroniser les paramètres entre les éditions et les produits de la famille Visual Studio

Vous pouvez synchroniser des paramètres dans toutes les éditions de Visual Studio, notamment la Community Edition. Les paramètres sont également synchronisés entre les produits de la famille Visual Studio. Toutefois, chacun de ces produits de famille peut avoir ses propres paramètres, lesquels ne sont pas partagés avec Visual Studio. Par exemple, les paramètres spécifiques à un produit sur l’ordinateur « A » sont partagés avec un autre produit sur l’ordinateur « B », mais pas avec Visual Studio sur les ordinateurs « A » ou « B ».

## <a name="side-by-side-synchronized-settings"></a>Paramètres synchronisés côte à côte

Dans Visual Studio 2017 version 15.3 et ultérieure, certains paramètres tels que la disposition de la fenêtre Outil ne sont pas partagés entre les différentes installations côte à côte de Visual Studio 2017. Le fichier *CurrentSettings.vssettings* dans *%userprofile%\Documents\Visual Studio 2017\Settings* se trouve dans un dossier spécifique à l’installation semblable à *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Pour utiliser les nouveaux paramètres spécifiques à l’installation, effectuez une nouvelle installation. Quand vous effectuez une mise à niveau d’une installation existante de Visual Studio 2017 vers la mise à jour la plus récente, elle utilise l’emplacement partagé existant.

Si vous disposez d’installations côte à côte de Visual Studio 2017 et si vous souhaitez utiliser le nouvel emplacement du fichier de paramètres spécifiques à l’installation, effectuez les étapes suivantes :

1. Effectuez une mise à niveau vers Visual Studio 2017 version 15.3 ou ultérieure.

1. Utilisez l’Assistant **Importation et exportation de paramètres** pour exporter tous vos paramètres existants vers un emplacement situé en dehors du dossier *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx*.

1. Ouvrez l’**Invite de commandes développeur pour VS 2017** correspondant à l’installation mise à niveau de Visual Studio, puis exécutez `devenv /resetuserdata`.

1. Lancez Visual Studio et importez les paramètres enregistrés du fichier de paramètres exportés.

## <a name="see-also"></a>Voir aussi

[Personnaliser l’IDE](../ide/personalizing-the-visual-studio-ide.md)
