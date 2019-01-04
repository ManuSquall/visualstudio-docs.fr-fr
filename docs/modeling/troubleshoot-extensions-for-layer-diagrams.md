---
title: Dépanner des extensions pour des diagrammes de dépendance
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d2a47bfd3b5ca927e64645f97f2923300e33d691
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926916"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Dépanner des extensions pour des diagrammes de dépendance

Cette rubrique aborde certains problèmes que vous pouvez rencontrer quand vous créez des extensions de modèle de couche.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>Lorsque j’appuie sur F5 pour déboguer mon extension, Mes commandes, gestionnaires de mouvements, extensions de validation ou des propriétés personnalisées n’apparaissent pas sur des diagrammes de dépendance dans l’instance expérimentale de Visual Studio

1. Ouvrez votre solution d’extension dans l’instance expérimentale de Visual Studio et sur le **Build** menu, cliquez sur **régénérer la Solution**.

2. Appuyez sur **F5** ou **CTRL + F5** pour démarrer l’instance expérimentale de Visual Studio. Ouvrez un diagramme de dépendance et testez votre extension.

   Continuez avec la procédure suivante si nécessaire.

## <a name="an-old-version-of-my-extension-runs"></a>Une ancienne version de mon extension s'exécute.

1. Assurez-vous qu’aucune instance expérimentale de Visual Studio n’est en cours d’exécution.

2. Supprimez le dossier suivant : %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache

   > [!NOTE]
   > %LocalAppData% est généralement *nom_lecteur*: \Users\\*nom d’utilisateur*\AppData\Local.

   Continuez avec la procédure suivante si nécessaire.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Une ancienne version de mes résultats de validation s'affiche ou ma méthode de validation n'est pas appelée.

1.  Dans l’instance expérimentale de Visual Studio, sur le **Build** menu, cliquez sur **nettoyer la Solution**. Cette opération efface les résultats mis en cache de l'analyse de validation précédente.

2.  Assurez-vous que les couches dans votre modèle sont associées à des éléments de code et qu'il existe au moins un lien de dépendance dans le modèle. La validation n'est pas appelée s'il n'y a rien à valider.

3.  Les points d'arrêt ordinaires peuvent ne pas fonctionner dans une méthode de validation, car elle s'exécute dans un processus séparé. Vous devez insérer un appel à `System.Diagnostics.Debugger.Launch()` si vous souhaitez parcourir votre méthode pas à pas.

4.  Dans **source.extension.vsixmanifest** dans votre projet de validation de couche, assurez-vous que vous avez ajouté à la fois un **composant MEF** élément et un **Type d’Extension personnalisée** sous **Contenu**.

## <a name="see-also"></a>Voir aussi

- [Extension des diagrammes de dépendance](../modeling/extend-layer-diagrams.md)
