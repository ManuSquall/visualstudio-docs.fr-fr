---
title: Valider votre modèle UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659374"
---
# <a name="validate-your-uml-model"></a>Valider votre modèle UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Certains des modèles UML que vous pouvez dessiner dans Visual Studio peuvent être considérés comme non valides dans votre projet. Par exemple, vous pouvez demander qu'un cas d'usage soit toujours lié à un diagramme de séquence comportant des lignes de vie qui représentent les acteurs du cas d'usage. Vous pouvez installer ou définir des *contraintes* qui permettent à votre équipe de se conformer à des exigences telles que celle-ci. Les contraintes peuvent être appliquées quand l'utilisateur enregistre ou ouvre un modèle, et appelées par une commande de menu.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] n'est pas fourni avec des contraintes, car celles-ci dépendent de la façon dont votre équipe interprète et utilise les modèles UML. Toutefois, vous pouvez définir vos propres contraintes et installer des contraintes définies par d'autres utilisateurs. Pour savoir comment définir des contraintes et les empaqueter en vue de leur distribution, consultez [définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="invoking-validation"></a>Appel de la validation
 Une fois que vous avez installé une extension de validation, les contraintes qu'elle fournit peuvent être appliquées dans les cas suivants. Certaines contraintes sont définies pour s'appliquer uniquement dans quelques-uns de ces cas.

- **Commande de validation.** Pour appeler la validation à tout moment, cliquez sur **valider le modèle UML** dans le menu **architecture** .

  > [!NOTE]
  > La commande s'affiche uniquement si les contraintes de validation sont installées.

- **Lors de l’enregistrement d’un modèle.** Les contraintes de validation peuvent être appliquées quand vous enregistrez le modèle. Ces contraintes visent à s'assurer que vous n'enregistrez pas un modèle non valide d'après l'interprétation de votre projet.

   Si des erreurs se produisent, il vous sera demandé si vous souhaitez toujours enregistrer le modèle. Vous pouvez choisir de corriger les erreurs ou d'enregistrer quand même le modèle.

- **Lors de l'ouverture d'un modèle.** Quand vous ouvrez un modèle, les méthodes de validation peuvent être appliquées pour restaurer les messages d'erreur qui existaient au moment de l'enregistrement du modèle. Des erreurs peuvent également être introduites par les incohérences qui résultent des modifications apportées par les utilisateurs travaillant sur différentes parties d'un modèle. Pour plus d’informations, consultez [partager des modèles et exportation de diagrammes](../modeling/share-models-and-exporting-diagrams.md).

  Les erreurs de validation sont signalées dans la fenêtre des erreurs de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

  Pour sélectionner les éléments incorrects dans un diagramme, double-cliquez sur l'erreur. Cette méthode fonctionne uniquement si les éléments incorrects sont visibles dans un diagramme ouvert.

## <a name="installing-validation-constraints"></a>Installation de contraintes de validation
 Les contraintes sont empaquetées dans des fichiers VSIX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension). En règle générale, un ensemble de contraintes fait partie d'une extension qui contient également d'autres définitions telles que des commandes de menu, des profils et des éléments de boîte à outils.

#### <a name="to-install-a-visual-studio-extension"></a>Pour installer une extension Visual Studio

1. Double-cliquez sur le fichier **. vsix** dans l’Explorateur Windows (ou l’Explorateur de fichiers).

2. Redémarrez toute instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui est déjà en cours d'exécution.

## <a name="disabling-and-uninstalling-validation-constraints"></a>Désactivation et désinstallation des contraintes de validation
 Quand vous voulez utiliser un modèle auquel les contraintes ne s'appliquent pas, vous pouvez désactiver temporairement l'extension qui les contient. De cette façon, vous pouvez travailler avec divers genres de modèles à des moments différents, en activant et en désactivant différentes extensions.

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Pour désactiver ou désinstaller une extension Visual Studio

1. Dans le menu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Outils**, cliquez sur **Extensions et mises à jour**.

2. En regard de l’extension, cliquez sur **Désactiver** pour désactiver temporairement l’extension. Vous pouvez la réactiver ultérieurement en revenant à la fenêtre **extensions et mises à jour** .

     \- ou -

     Cliquez sur **désinstaller** pour supprimer l’extension.

3. Redémarrez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Voir aussi
 [Définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md) [créer des modèles pour votre application](../modeling/create-models-for-your-app.md) [utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)
