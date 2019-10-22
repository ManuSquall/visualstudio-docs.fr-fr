---
title: Résoudre les problèmes liés aux extensions pour les diagrammes de couche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658473"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Dépanner les extensions des diagrammes de couche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique aborde certains problèmes que vous pouvez rencontrer quand vous créez des extensions de modèle de couche.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Quand j'appuie sur F5 pour déboguer mon extension, mes commandes, gestionnaires de mouvements, extensions de validation ou propriétés personnalisées n'apparaissent pas sur les diagrammes de couche dans l'instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

1. Ouvrez votre solution d’extension dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et, dans le menu **générer** , cliquez sur **régénérer la solution**.

2. Appuyez sur **F5** ou sur **CTRL + F5** pour démarrer l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ouvrez un diagramme de couche et testez votre extension.

   Continuez avec la procédure suivante si nécessaire.

#### <a name="an-old-version-of-my-extension-runs"></a>Une ancienne version de mon extension s'exécute.

1. Assurez-vous qu'aucune instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] n'est en cours d'exécution.

2. Supprimez le dossier suivant :%LocalAppData%\Microsoft\VisualStudio \\ [version] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData% *est généralement le*nom de la \AppData\Local. : \Utilisateurs \\*nom_utilisateur*

   Continuez avec la procédure suivante si nécessaire.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Une ancienne version de mes résultats de validation s'affiche ou ma méthode de validation n'est pas appelée.

1. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dans le menu **générer** , cliquez sur **nettoyer la solution**. Cette opération efface les résultats mis en cache de l'analyse de validation précédente.

2. Assurez-vous que les couches dans votre modèle sont associées à des éléments de code et qu'il existe au moins un lien de dépendance dans le modèle. La validation n'est pas appelée s'il n'y a rien à valider.

3. Les points d'arrêt ordinaires peuvent ne pas fonctionner dans une méthode de validation, car elle s'exécute dans un processus séparé. Vous devez insérer un appel à `System.Diagnostics.Debugger.Launch()` si vous souhaitez parcourir votre méthode pas à pas.

4. Dans **source. extension. vsixmanifest** dans votre projet de validation de couche, vérifiez que vous avez ajouté un élément de **Composant MEF** et un élément de **type d’extension personnalisé** sous **contenu**.

## <a name="see-also"></a>Voir aussi
 [Étendre des diagrammes de couche](../modeling/extend-layer-diagrams.md)
