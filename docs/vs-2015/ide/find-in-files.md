---
title: Rechercher dans les fichiers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e1d9c456c22b4d3003d9435f813a4c3c1dc47881
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383385"
---
# <a name="find-in-files"></a>Rechercher dans les fichiers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option Rechercher dans les fichiers** vous permet de faire des recherches dans un ensemble défini de fichiers. Les correspondances trouvées et les actions entreprises sont répertoriées dans la fenêtre **Résultats de la recherche** sélectionnée dans **Options de résultat**.  
  
 Vous pouvez utiliser l’une des méthodes suivantes pour afficher l’option **Rechercher dans les fichiers** de la fenêtre **Rechercher et remplacer**.  
  
### <a name="to-display-find-in-files"></a>Pour afficher l'option Rechercher dans les fichiers  
  
1. Dans la barre de menus, choisissez **Edition**, puis **Rechercher et remplacer**.  
  
2. Choisissez **Rechercher dans les fichiers**.  
  
   Pour annuler une opération de recherche, appuyez sur Ctrl+Pause.  
  
> [!NOTE]
> L'outil Rechercher et remplacer n'effectue pas de recherche dans les répertoires définis avec l'attribut `Hidden` ou `System`.  
  
## <a name="find-what"></a>Rechercher  
 Pour rechercher une nouvelle chaîne de texte ou expression, entrez-la dans cette zone. Pour rechercher une des 20 dernières chaînes que vous avez recherchées récemment, ouvrez la liste et sélectionnez la chaîne à rechercher. Choisissez le bouton adjacent **Générateur d’expressions** si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de recherche. Pour plus d’informations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Regarder dans  
 L’option choisie dans la liste déroulante **Regarder dans** détermine si l’opération **Rechercher dans les fichiers** porte sur les fichiers actifs uniquement ou sur tous les fichiers figurant dans certains dossiers. Sélectionnez une étendue de recherche dans la liste ou cliquez sur le bouton **Parcourir (...)** pour afficher la boîte de dialogue **Choisir des dossiers de recherche** et spécifier l’ensemble de répertoires de votre choix. Vous pouvez également taper un chemin directement dans la zone **Regarder dans**.  
  
> [!WARNING]
> Avec les options **Solution complète** ou **Projet actuel**, les fichiers solution et projet ne sont pas inclus dans la recherche. Pour effectuer une recherche dans les fichiers projet, choisissez un dossier de recherche.  
  
> [!NOTE]
> Si l’option **Regarder dans** sélectionnée entraîne la recherche dans un fichier que vous avez extrait du contrôle de code source, la recherche ne porte que sur la version du fichier ayant été téléchargée sur votre ordinateur local.  
  
## <a name="include-subfolders"></a>Inclure les sous-dossiers  
 Spécifie que les sous-dossiers du dossier choisi dans **Regarder dans** sont inclus dans la recherche.  
  
## <a name="find-options"></a>Options de recherche  
 Vous pouvez développer ou réduire la section **Options de recherche**. Les options suivantes peuvent être sélectionnées ou désélectionnées :  
  
 Respecter la casse  
 Si vous sélectionnez cette option, la fenêtre **Résultats de la recherche** affiche uniquement les correspondances qui respectent la casse.  
  
 Mot entier  
 Si vous sélectionnez cette option, la fenêtre **Résultats de la recherche** affiche uniquement les correspondances de mot entier.  
  
 Utiliser des expressions régulières  
 Si cette case est cochée, vous pouvez utiliser des notations spéciales pour définir des modèles de texte à rechercher dans les zones de texte **Rechercher** ou **Remplacer par**. Pour obtenir la liste de ces notations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Examiner ces types de fichiers  
 Cette liste indique les types de fichiers à examiner dans les répertoires choisis dans **Regarder dans**. Si ce champ est laissé vide, tous les fichiers présents dans les répertoires choisis dans **Regarder dans** sont examinés.  
  
 Sélectionnez un élément dans la liste pour entrer une chaîne de recherche prédéfinie à rechercher dans les fichiers de ces types particuliers.  
  
## <a name="result-options"></a>Options de résultat  
 Vous pouvez développer ou réduire la section **Options de résultat**. Les options suivantes peuvent être sélectionnées ou désélectionnées :  
  
 Fenêtre Résultats de la recherche 1  
 Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 1**. Cette fenêtre s'ouvre automatiquement pour afficher les résultats de votre recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 1**.  
  
 Fenêtre Résultats de la recherche 2  
 Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 2**. Cette fenêtre s'ouvre automatiquement pour afficher les résultats de votre recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 2**.  
  
 Afficher uniquement les noms de fichier  
 Affiche une liste des fichiers contenant des correspondances de recherche au lieu d'afficher les correspondances elles-mêmes.  
  
 Ajouter les résultats  
 Ajoute les résultats de la recherche actuelle aux résultats des recherches précédentes.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)   
 [Remplacer dans les fichiers](../ide/replace-in-files.md)   
 [Commandes Visual Studio](../ide/reference/visual-studio-commands.md)
