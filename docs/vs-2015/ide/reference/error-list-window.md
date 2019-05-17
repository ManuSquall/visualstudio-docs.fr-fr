---
title: Liste d’erreurs, fenêtre | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d481bbc71019639588c793fee64acd34d5739e8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680147"
---
# <a name="error-list-window"></a>Liste d'erreurs, fenêtre
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

REMARQUE]
> La liste d'erreurs affiche des informations sur un message d'erreur spécifique. Vous pouvez copier le numéro d'erreur ou le texte de la chaîne d'erreur dans la fenêtre Sortie. Pour afficher la fenêtre Sortie, appuyez sur Ctrl+Alt+O. Consultez [Sortie, fenêtre](../../ide/reference/output-window.md).  
  
 La fenêtre **Liste d’erreurs** permet d’accélérer le développement des applications. Par exemple, il est possible de réaliser les tâches suivantes :  
  
- afficher les erreurs, avertissements et messages générés pendant l'écriture du code ;  
  
- rechercher les erreurs de syntaxe relevées par IntelliSense ;  
  
- rechercher les erreurs de déploiement, certaines erreurs d'analyse statique et les erreurs détectées lors de l'application de stratégies de modèle d'entreprise ;  
  
- double-cliquer sur toute entrée de message d'erreur pour ouvrir le fichier où le problème se produit et accéder à l'emplacement de l'erreur ;  
  
- filtrer les entrées qui sont affichées et les colonnes d'information qui apparaissent pour chaque entrée ;  
  
- rechercher des termes spécifiques et limiter la recherche au projet ou au document actif.  
  
  Pour afficher la **Liste d’erreurs**, cliquez sur **Afficher/Liste d’erreurs** ou appuyez sur **CTRL+\\+E**.  
  
  Vous pouvez choisir les onglets **Erreurs**, **Avertissements** et **Messages** pour afficher les différents niveaux d’informations.  
  
  Pour trier la liste, cliquez sur n'importe quel en-tête de colonne. Pour trier à nouveau sur une colonne supplémentaire, maintenez la touche Maj enfoncée et cliquez sur un autre en-tête de colonne. Pour sélectionner les colonnes qui doivent être affichées et celles qui doivent être masquées, choisissez **Afficher les colonnes** dans le menu contextuel. Pour modifier l'ordre dans lequel les colonnes sont affichées, faites glisser les en-têtes de votre choix vers la droite ou la gauche.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites ici, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, cliquez sur **Outils/Importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="error-list-filters"></a>Filtres de la liste d'erreurs  
 Il existe deux types de filtre dans deux zones de liste déroulante, l’un à droite de la barre d’outils, et l’autre à gauche de la barre d’outils. La liste déroulante située à gauche de la barre d’outils spécifie l’ensemble de fichiers de code à utiliser (**Solution complète**, **Documents ouverts**, **Projet actif**, **Document actif**).  
  
 Vous pouvez restreindre la portée de la recherche pour analyser et agir sur des groupes d'erreurs. Par exemple, vous pouvez vous concentrer sur les erreurs principales qui empêchent la compilation d'un projet. Les options de portée disponibles sont les suivantes :  
  
1. **Documents ouverts** : afficher les erreurs, les avertissements et les messages relatifs aux documents ouverts.  
  
2. **Projet actif** : afficher les erreurs, les avertissements et les messages du projet du document actuellement sélectionné dans l’**Éditeur** ou du projet sélectionné dans l’**Explorateur de solutions**.  
  
   > [!NOTE]
   > La liste filtrée d’erreurs, d’avertissements et de messages est modifiée si le projet du document actuellement sélectionné est différent du projet sélectionné dans l’**Explorateur de solutions**.  
  
3. **Document actif** : afficher les erreurs, les avertissements et les messages du document actuellement sélectionné dans l’**Éditeur** ou dans l’**Explorateur de solutions**.  
  
   Si un filtre est actuellement appliqué aux résultats de la recherche, le nom du filtre apparaît dans la barre de titre **Liste d’erreurs**. Les boutons **Erreurs**, **Avertissements** et **Messages** affichent alors le nombre d’éléments filtrés affichés, ainsi que le nombre total d’éléments ; par exemple, les boutons indiquent x erreurs sur y. Si aucun filtre n'est appliqué, la barre de titre indique uniquement « Liste d'erreurs ».  
  
   La liste située à droite de la barre d'outils indique si les erreurs doivent être affichées à partir de la build (erreurs résultant d'une opération de build) ou à partir d'IntelliSense (erreurs détectées avant d'exécuter une build), ou les deux.  
  
## <a name="search"></a>Rechercher  
 Utilisez la zone de texte **Rechercher dans la liste des erreurs** située à droite de la barre d’outils **Liste d’erreurs** pour rechercher des erreurs spécifiques dans la liste d’erreurs. Vous pouvez rechercher sur toute colonne visible dans la liste et les résultats de la recherche sont toujours triés selon la colonne de tri prioritaire au lieu de la requête ou du filtre appliqué. Si vous choisissez la touche **Échap** tandis que le focus est dans la **Liste d’erreurs**, vous pouvez effacer le terme de recherche et les résultats de la recherche filtrés. Vous pouvez également cliquer sur la croix (**X**) à droite de la zone de texte pour l’effacer.  
  
## <a name="save"></a>Enregistrer  
 Vous pouvez copier la liste d'erreurs et l'enregistrer dans un fichier. Sélectionnez les erreurs que vous voulez copier, cliquez avec le bouton droit sur la sélection, puis, dans le menu contextuel, sélectionnez **Copier**. Vous pouvez ensuite coller les erreurs dans un fichier. Si vous collez les erreurs dans une feuille de calcul Excel, les champs apparaissent comme colonnes individuelles.  
  
## <a name="ui-element-list"></a>Liste des éléments de l'interface utilisateur  
 Gravité  
 Affiche les différents types d’entrée de la **Liste d’erreurs** (**Erreur**, **Message**, **Avertissement**, **Avertissement (actif)**, **Avertissement (inactif)**).  
  
 Code  
 Affiche le code d'erreur.  
  
 Description  
 Affiche le texte de l'entrée.  
  
 Projet  
 Affiche le nom du projet actif.  
  
 Fichier  
 Affiche le nom de fichier.  
  
 Ligne  
 Affiche la ligne où apparaît le problème.
