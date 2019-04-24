---
title: Documents, Environnement, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ba05030a0f842d6905be384739a9d797634092f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652629"
---
# <a name="documents-environment-options-dialog-box"></a>Documents, Environnement, boîte de dialogue Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez cette page de la boîte de dialogue **Options** pour contrôler l’affichage des documents dans l’environnement de développement intégré (IDE) et pour gérer les modifications externes apportées aux documents et aux fichiers. Vous pouvez accéder à cette boîte de dialogue en cliquant sur **Options** dans le menu **Outils**, puis en sélectionnant **Documents** dans le nœud **Environnement**. Si **Documents** ne figure pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.  
  
> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Réutiliser la fenêtre du document actif, si elle a été enregistrée**  
 Lorsque cette option est sélectionnée, votre document actif est fermé s’il a été enregistré et un nouveau document est ouvert dans la même fenêtre. Si votre document actif n’a pas été enregistré, il reste ouvert et le nouveau document est ouvert dans une fenêtre distincte. Lorsque cette option est désactivée, les nouveaux documents s’ouvrent toujours dans des fenêtres distinctes.  
  
 Si vous effectuez rarement des opérations de couper-coller sur plusieurs documents et souhaitez réduire le plus possible le nombre de fenêtres et de documents ouverts dans votre espace de travail, essayez cette option.  
  
 **Détecter lorsqu’un fichier est modifié en dehors de l’environnement**  
 Lorsque cette option est sélectionnée, un message vous avertit immédiatement des modifications qui ont été apportées par un éditeur à un fichier ouvert en dehors de l’IDE. Le message vous permet de recharger le fichier à partir de l’espace de stockage.  
  
 **Charger automatiquement les modifications, si elles ont été enregistrées**  
 Lorsque l’option **Détecter lorsqu’un fichier est modifié en dehors de l’environnement** est sélectionnée et qu’un fichier ouvert dans l’IDE est modifié en dehors de l’IDE, un message d’avertissement est généré par défaut. Si cette option est activée, aucun avertissement n’apparaît et le document est rechargé dans l’IDE pour relever les modifications externes.  
  
 **Autoriser la modif. des fichiers en lecture seule ; avertir à l’enregistrement**  
 Lorsque cette option est activée, vous pouvez ouvrir et modifier un fichier en lecture seule. Lorsque vous avez terminé, vous devez utiliser la commande **Enregistrer sous** pour enregistrer le fichier sous un nouveau nom si vous souhaitez conserver un enregistrement de vos modifications.  
  
 **Ouvrir un fichier à partir du répertoire du document actif**  
 Lorsque cette option est sélectionnée, le boîte de dialogue **Ouvrir le fichier** affiche le répertoire du document actif. Lorsque cette option est désactivée, la boîte de dialogue **Ouvrir le fichier** affiche le dernier répertoire utilisé pour ouvrir un fichier.  
  
 **Vérifier la cohérence des fins de ligne au chargement**  
 Sélectionnez cette option pour que l’éditeur analyse les fins de ligne dans un fichier et affiche une boîte de message si des incohérences sont détectées dans le format des fins de ligne.  
  
 **Afficher un avertissement lorsqu’une annulation globale affecte des fichiers modifiés**  
 Sélectionnez cette option pour afficher une boîte de message lorsque la commande **Annulation globale** restaure les modifications de refactorisation effectuées dans des fichiers qui ont également été modifiés après l’opération de refactorisation. Le renvoi d’un fichier à son état antérieur à la refactorisation peut annuler les modifications ultérieures apportées dans le fichier.  
  
 **Afficher les fichiers divers dans l’Explorateur de solutions**  
 Sélectionnez cette option pour afficher le nœud **Fichiers divers** dans l’**Explorateur de solutions**. Les fichiers divers sont des fichiers qui ne sont pas associés à un projet ou une solution, mais qui peuvent apparaître dans l’**Explorateur de solutions** à toutes fins utiles.  
  
> [!NOTE]
>  Sélectionnez cette option pour activer la commande **Afficher dans le navigateur** dans le menu **Fichier** pour les documents web non inclus dans l’application web active.  
  
 **\<** *n* **> éléments enregistrés dans le projet Fichiers divers**  
 Spécifie le nombre de fichiers à rendre persistants dans le dossier **MiscellaneousFiles** de l’**Explorateur de solutions**. Ces fichiers sont répertoriés même s’ils ne sont plus ouverts dans un éditeur. Vous pouvez spécifier n’importe quel nombre entier compris entre 0 et 256. Le nombre par défaut est 0.  
  
 Par exemple, si vous définissez cette option sur 5 et avez ouvert 10 fichiers divers, lorsque vous fermez les 10 fichiers, les 5 premiers restent affichés dans le dossier **Fichiers divers**.  
  
 **Enregistrer les documents au format Unicode lorsque les données ne peuvent pas être enregistrées dans la page de codes**  
 Sélectionnez cette option pour enregistrer au format Unicode par défaut les fichiers contenant des informations incompatibles avec la page de codes sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)   
 [Fichiers divers](../../ide/reference/miscellaneous-files.md)   
 [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md)
