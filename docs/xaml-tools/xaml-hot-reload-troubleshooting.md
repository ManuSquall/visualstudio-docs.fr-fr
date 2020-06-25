---
title: Résolution des problèmes de rechargement à chaud XAML
description: Résolvez les problèmes que vous pouvez rencontrer avec le rechargement à chaud XAML.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 447725fd27ab81b85890d37a8f0df8a35ad5fbee
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328471"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Résolution des problèmes de rechargement à chaud XAML

Ce guide de dépannage contient des instructions détaillées qui doivent résoudre la plupart des problèmes qui empêchent le rechargement à chaud XAML de fonctionner correctement.

Le rechargement à chaud XAML est pris en charge pour les applications WPF et UWP. Pour plus d’informations sur les exigences relatives aux outils et au système d’exploitation, consultez [écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>Le rechargement à chaud n’est pas disponible

Si vous voyez le message « le rechargement à chaud n’est pas disponible » dans la barre d’outils de l’application pendant le débogage de votre application, suivez les instructions décrites dans cet article pour résoudre le problème.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Vérifier que le rechargement à chaud XAML est activé

La fonctionnalité est activée par défaut. Lorsque vous commencez à déboguer votre application, assurez-vous que la barre d’outils dans l’application s’affiche, ce qui confirme que le rechargement à chaud XAML est disponible :

![Rechargement à chaud XAML disponible](../debugger/media/xaml-hot-reload-available.png)

Si vous ne voyez pas la barre d’outils dans l’application, ouvrez Options de **débogage**  >  **Options**  >  **général**. Assurez-vous que les deux options, **activer les outils de débogage de l’interface utilisateur pour XAML** et **activer le rechargement à chaud XAML** sont sélectionnées.

![Activer le rechargement à chaud XAML](../debugger/media/xaml-hot-reload-enable.png)

Si ces options sont sélectionnées, accédez à l’arborescence d’éléments visuels dynamique (**Déboguer**  >  **Windows**  >  l’arborescence d’éléments**visuels Windows Live**) et assurez-vous que l’option Afficher les outils d' **exécution dans** la barre d’outils de l’application (à l’extrême gauche) est sélectionnée.

![Activer le rechargement à chaud XAML](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Vérifier que vous utilisez démarrer le débogage plutôt que attacher au processus

Le rechargement à chaud XAML nécessite que la variable `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` d’environnement soit définie sur 1 au moment du démarrage de l’application. Visual Studio définit cela automatiquement dans le cadre de **la commande Déboguer**  >  **Démarrer le débogage** (ou **F5**). Si vous souhaitez utiliser à la place le rechargement à chaud XAML avec la commande **Déboguer**  >  **attacher au processus** , définissez la variable d’environnement vous-même.

> [!NOTE]
> Pour définir une variable d’environnement, utilisez le bouton Démarrer pour rechercher « variable d’environnement », puis choisissez **modifier les variables d’environnement système**. Dans la boîte de dialogue qui s’ouvre, choisissez **variables d’environnement**, ajoutez-la en tant que variable utilisateur, puis affectez la valeur à `1` . Pour nettoyer, supprimez la variable lorsque vous avez terminé le débogage.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Vérifier que vos propriétés MSBuild sont correctes

Par défaut, les informations sur la source sont incluses dans une configuration de débogage. Il est contrôlé par les propriétés MSBuild dans vos fichiers projet (tels que *. csproj). Pour WPF, la propriété est `XamlDebuggingInformation` , qui doit avoir la valeur `True` . Pour UWP, la propriété est `DisableXbfLineInfo` , qui doit avoir la valeur `False` . Par exemple :

WPF :

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Vérifier que vous utilisez le nom correct de la configuration de build

Vous devez soit définir manuellement la propriété MSBuild appropriée pour prendre en charge le rechargement à chaud XAML (voir la section précédente), soit utiliser le nom de configuration de build par défaut (Debug). Si vous ne définissez pas correctement la propriété MSBuild, un nom de configuration de build personnalisé ne fonctionnera pas, ni une version Release.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Vérifier que votre fichier XAML n’a pas d’erreurs

Si votre fichier XAML affiche des erreurs dans le **liste d’erreurs**, le rechargement à chaud XAML peut ne pas fonctionner.

## <a name="see-also"></a>Voir aussi

[Écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML](xaml-hot-reload.md)
