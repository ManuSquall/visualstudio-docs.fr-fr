---
title: Divers, XML, éditeur de texte, boîte de dialogue Options | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccbdfae65792fb6816a0604db6339a9d63fa2ccb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Divers, XML, Éditeur de texte, boîte de dialogue Options
Cette boîte de dialogue permet de modifier les paramètres de saisie semi-automatique et de schéma de l'éditeur XML. Vous pouvez accéder à la **Options** boîte de dialogue à partir de la **outils** menu.  
  
> [!NOTE]
>  Ces paramètres sont disponibles lorsque vous sélectionnez le **éditeur de texte** dossier, le **XML** dossier, puis le **divers** option à partir de la **Options** boîte de dialogue.  
  
## <a name="auto-insert"></a>Insertion automatique  
 **Balises de fermeture**  
 Si le paramètre de saisie semi-automatique est sélectionné, l’éditeur ajoute automatiquement une étiquette de fin lorsque vous tapez un crochet pointu droit (>) pour fermer une étiquette de début, si l’étiquette n’est pas déjà fermée. Il s'agit du comportement par défaut.  
  
 La saisie d'un élément vide ne dépend pas du paramètre de saisie semi-automatique. Vous pouvez toujours effectuer la saisie semi-automatique d'un élément vide en tapant une barre oblique inverse (/).  
  
 **Guillemets d’attribut**  
 Lorsque vous éditez des attributs XML, l'éditeur insère les caractères `=" "` et place le signe ^ à l'intérieur des guillemets doubles.  
  
 Cette option est sélectionnée par défaut.  
  
 **Déclarations d’espaces de noms**  
 L'éditeur insère automatiquement des déclarations d'espaces de noms chaque fois qu'elles sont nécessaires.  
  
 Cette option est sélectionnée par défaut.  
  
 **Autre balisage (commentaires, CDATA)**  
 Les commentaires, CDATA, DOCTYPE, instructions de traitement et autres balisages sont automatiquement complétés.  
  
 Cette option est sélectionnée par défaut.  
  
## <a name="network"></a>Réseau  
 **Télécharger automatiquement les DTD et les schémas**  
 Les schémas et les DTD (définitions de type de document) sont automatiquement téléchargés à partir d'emplacements HTTP. Cette fonction utilise System.Net avec la détection automatique de serveur proxy activée.  
  
 Cette option est sélectionnée par défaut.  
  
## <a name="outlining"></a>mode Plan  
 **Passer en mode Plan à l’ouverture des fichiers**  
 Active la fonctionnalité mode plan à l’ouverture d’un fichier.  
  
 Cette option est sélectionnée par défaut.  
  
## <a name="caching"></a>Mise en cache  
 **Schémas**  
 Spécifie l'emplacement du cache de schéma. Le bouton Parcourir (**...** ) ouvre le **parcourir les répertoires** boîte de dialogue à l’emplacement du cache de schéma en cours. Vous pouvez sélectionner un autre répertoire, ou vous pouvez sélectionner un dossier dans la boîte de dialogue, avec le bouton droit, puis choisissez **ouvrir** pour voir ce qui se trouve dans le répertoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)   
 [Composants de l’éditeur XML](../xml-tools/xml-editor-components.md)