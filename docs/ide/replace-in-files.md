---
title: "Remplacer dans les fichiers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findreplace.replaceinfiles"
  - "vs.replaceinfiles"
helpviewer_keywords: 
  - "recherches de texte, remplacement de texte"
  - "Rechercher et remplacer (fenêtre), onglet Remplacer dans les fichiers"
  - "Remplacer dans les fichiers (onglet), fenêtre Rechercher et remplacer"
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Remplacer dans les fichiers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Remplacer dans les fichiers** permet de rechercher une chaîne ou une expression dans le code d'un ensemble défini de fichiers, et de modifier tout ou partie des correspondances trouvées.  Les correspondances trouvées et les actions prises sont répertoriées dans la fenêtre **Résultats de la recherche** sélectionnée dans **Options de résultat**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Vous pouvez utiliser l'une des méthodes suivantes pour afficher **Remplacer dans les fichiers** dans la fenêtre **Rechercher et remplacer**.  
  
### Pour afficher Remplacer dans les fichiers  
  
1.  Dans le menu **Edition**, développez **Rechercher et remplacer**.  
  
2.  Choisissez **Remplacer dans les fichiers**.  
  
     – ou –  
  
     Si la  **Rechercher et remplacer** fenêtre est déjà ouverte, dans la barre d'outils, choisissez  **Remplacer dans les fichiers**.  
  
## Rechercher  
 Pour rechercher une nouvelle chaîne de texte ou une expression, vous devez le spécifier dans la zone.  Pour rechercher une des 20 chaînes que vous avez recherché plus récemment, ouvrir la liste, puis choisissez la chaîne pour laquelle vous souhaitez rechercher.  Choisissez la zone adjacente  **Générateur d'Expression** bouton si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de recherche.  Pour plus d'informations, consultez [Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Remplacer par  
 Pour remplacer les instances de la chaîne dans le  **Rechercher** avec une autre chaîne, entrez la chaîne de remplacement dans la  **Remplacer par** boîte.  Pour supprimer les instances de la chaîne dans le  **Rechercher** zone, laissez ce champ vide.  Ouvrez la liste pour afficher les 20 chaînes que vous avez recherché plus récemment.  Choisissez la zone adjacente  **Générateur d'Expression** bouton si vous souhaitez utiliser une ou plusieurs expressions régulières dans la chaîne de remplacement.  Pour plus d'informations, consultez [Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Regarder dans  
 L'option choisie dans la liste déroulante **Regarder dans** détermine si la recherche de **Remplacer dans les fichiers** s'effectue uniquement dans les fichiers actifs ou dans tous les fichiers stockés dans certains dossiers.  Sélectionnez une étendue de recherche dans la liste, tapez un chemin d'accès au dossier ou cliquez sur le  **Parcourir \(...\)** bouton pour afficher la  **Choisir des dossiers de recherche** boîte de dialogue zone, puis choisissez un ensemble de dossiers à rechercher.  Vous pouvez également entrer un chemin d'accès directement dans la zone **Regarder dans**.  
  
> [!NOTE]
>  Si l'option **Regarder dans** sélectionnée entraîne la recherche dans un fichier que vous avez extrait du contrôle de code source, seule la version de ce fichier qui a été téléchargée sur votre ordinateur local sera parcourue.  
  
## Options de recherche  
 Vous pouvez développer ou réduire la section **Options de recherche**.  Les options suivantes peuvent être activées ou désactivées :  
  
 Respecter la casse  
 Lorsque vous sélectionnez cette option, les fenêtres **Résultats de la recherche** afficheront seulement les instances de la chaîne **Rechercher** dont le contenu et la casse sont identiques.  Par exemple, la recherche de "MyObject" avec l'option **Respecter la casse** sélectionnée retourne "MyObject", mais pas "myobject" ni "MYOBJECT".  
  
 Mot entier  
 Lorsque vous sélectionnez cette option, les fenêtres **Résultats de la recherche** afficheront seulement les instances de la chaîne **Rechercher** contenant les mêmes mots entiers.  Par exemple, la recherche de "MyObject" retourne "MyObject", mais pas "CMyObject" ni "MyObjectC".  
  
 Utiliser des Expressions régulières  
 Lorsque cette case à cocher est activée, vous pouvez utiliser les notations spéciales pour définir des modèles de texte dans le  **Rechercher** ou  **Remplacer par** les zones de texte.  Pour obtenir une liste de ces notations, voir [Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Examiner ces types de fichiers  
 Cette liste indique les types de fichiers à examiner dans les répertoires associés à **Regarder dans**.  Si ce champ est laissé vide, tous les fichiers des répertoires associés à **Regarder dans** sont examinés.  
  
 Sélectionnez un élément dans la liste pour entrer une chaîne de recherche préconfigurée qui recherchera les fichiers correspondant à ces types particuliers.  
  
## Options de résultat  
 Vous pouvez développer ou réduire la section **Options de résultat**.  Les options suivantes peuvent être activées ou désactivées :  
  
 Fenêtre Résultats de la recherche 1  
 Une fois sélectionnés, les résultats de la recherche en cours remplacent le contenu de la fenêtre **Résultats de la recherche 1**.  Cette fenêtre s'ouvre automatiquement pour afficher les résultats de votre recherche.  Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 1**.  
  
 Fenêtre Résultats de la recherche 2  
 Une fois sélectionnés, les résultats de la recherche en cours remplacent le contenu de la fenêtre **Résultats de la recherche 2**.  Cette fenêtre s'ouvre automatiquement pour afficher les résultats de votre recherche.  Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 2**.  
  
 Afficher les noms des fichiers seulement  
 Lorsque cette case à cocher est activée, les fenêtres résultats de la recherche répertorient les noms complets et les chemins d'accès pour tous les fichiers qui contiennent la chaîne de recherche.  Toutefois, les résultats ne contiennent pas la ligne de code où apparaît la chaîne.  Cette case à cocher n'est disponible pour rechercher dans les fichiers.  
  
 Conserver les fichiers modifiés ouverts après un remplacement global  
 Lorsque cette option est sélectionnée, tous les fichiers dans lesquels des remplacements ont été effectués restent ouverts et vous pouvez ainsi annuler ou enregistrer les modifications.  Les contraintes de mémoire peuvent limiter le nombre de fichiers qui peuvent rester ouverts suite à une opération de remplacement.  
  
> [!CAUTION]
>  Vous ne pouvez utiliser **Annuler** que sur les fichiers qui restent ouverts.  Si cette option n'est pas sélectionnée, les fichiers qui n'étaient pas déjà ouverts restent fermés, et aucune option **Annuler** n'est disponible dans ces fichiers.  
  
## Voir aussi  
 [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)   
 [Rechercher dans les fichiers](../ide/find-in-files.md)   
 [Commandes Visual Studio](../ide/reference/visual-studio-commands.md)