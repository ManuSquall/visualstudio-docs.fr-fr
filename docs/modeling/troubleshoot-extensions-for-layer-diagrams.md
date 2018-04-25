---
title: Dépanner les extensions de diagrammes de dépendance
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
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5f284ddf548e48469e97b44fa2f4524c818b4cf4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Dépanner les extensions de diagrammes de dépendance

Cette rubrique aborde certains problèmes que vous pouvez rencontrer quand vous créez des extensions de modèle de couche.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Lorsque vous appuyez sur F5 pour déboguer mon extension, Mes commandes, les gestionnaires de mouvements, les extensions de validation ou des propriétés personnalisées n’apparaissent pas sur les diagrammes de dépendance dans l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

1.  Ouvrez votre solution d’extension dans l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puis, dans le **générer** menu, cliquez sur **régénérer la Solution**.

2.  Appuyez sur **F5** ou **CTRL + F5** pour démarrer l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ouvrir un diagramme de dépendances et tester votre extension.

 Continuez avec la procédure suivante si nécessaire.

## <a name="an-old-version-of-my-extension-runs"></a>Une ancienne version de mon extension s'exécute.

1.  Assurez-vous qu'aucune instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n'est en cours d'exécution.

2.  Supprimez le dossier suivant : %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache

    > [!NOTE]
    > %LocalAppData% est généralement *%drivename*: \Users\\*nom d’utilisateur*\AppData\Local.

 Continuez avec la procédure suivante si nécessaire.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Une ancienne version de mes résultats de validation s'affiche ou ma méthode de validation n'est pas appelée.

1.  Dans l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dans le **générer** menu, cliquez sur **nettoyer la Solution**. Cette opération efface les résultats mis en cache de l'analyse de validation précédente.

2.  Assurez-vous que les couches dans votre modèle sont associées à des éléments de code et qu'il existe au moins un lien de dépendance dans le modèle. La validation n'est pas appelée s'il n'y a rien à valider.

3.  Les points d'arrêt ordinaires peuvent ne pas fonctionner dans une méthode de validation, car elle s'exécute dans un processus séparé. Vous devez insérer un appel à `System.Diagnostics.Debugger.Launch()` si vous souhaitez parcourir votre méthode pas à pas.

4.  Dans **source.extension.vsixmanifest** dans votre projet de validation de couche, assurez-vous que vous avez ajouté à la fois un **composant MEF** élément et un **Type d’Extension personnalisée** d’élément sous **Contenu**.

## <a name="see-also"></a>Voir aussi

- [Extension des diagrammes de dépendance](../modeling/extend-layer-diagrams.md)
