---
title: "Documents, Environnement, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Environment.Documents"
  - "VS.ToolsOptionsPages.Environment.Documents"
  - "VS.ToolsOptionsPag.Environment.Documents"
helpviewer_keywords: 
  - "Documents, Environnement (boîte de dialogue Options)"
  - "par défaut, répertoires"
  - "messages d’erreur, personnalisation"
  - "fichiers (Visual Studio), options par défaut"
  - "fichiers (Visual Basic), chargement automatique modifié"
  - "fenêtres, personnalisation de l’environnement"
  - "modification en mémoire"
  - "dossiers (Visual Studio), spécification de l’emplacement Ouvrir un fichier"
  - "Ouvrir un fichier (boîte de dialogue)"
  - "fenêtres, activation de la réutilisation des fenêtres actives"
  - "notifications, fichiers modifiés"
  - "fichiers (Visual Studio), affichage dans l’Explorateur de solutions"
  - "répertoires par défaut"
  - "fichiers en lecture seule, modification"
  - "Options (boîte de dialogue), affichage de Fichiers divers"
  - "répertoires (Visual Studio), options d’environnement IDE"
  - "Options (boîte de dialogue), page Documents"
  - "avertissements, fichiers modifiés"
  - "Explorateur de solutions, affichage des fichiers dans"
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Documents, Environnement, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette page de la boîte de dialogue **Options** vous permet de contrôler l'affichage de documents et fichiers dans l'environnement de développement intégré \(IDE, Integrated Development Environment\) et de gérer les modifications externes apportées aux documents et aux fichiers.  Vous pouvez accéder à cette boîte de dialogue en cliquant sur **Options** dans le menu **Outils**, puis en sélectionnant **Documents** dans le nœud **Environnement**.  Si **Documents** n'apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.  
  
> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Réutiliser la fenêtre du document actif, si elle a été enregistrée**  
 Une fois sélectionnée, cette option ferme le document actif s'il a été enregistré et ouvre un nouveau document dans la même fenêtre.  Si le document actif n'a pas été enregistré, il reste ouvert et le nouveau document s'ouvre dans une fenêtre distincte.  Lorsque cette option est désactivée, les nouveaux documents s'ouvrent systématiquement dans des fenêtres distinctes.  
  
 Si vous n'exécutez pas fréquemment des opérations de copier\-coller dans plusieurs documents et que vous souhaitez réduire le nombre de fenêtres et de documents ouverts dans votre espace de travail, essayez cette option.  
  
 **Détecter quand le fichier est modifié en dehors de l'environnement**  
 Lorsque cette option est activée, un message vous avertit immédiatement des modifications apportées à un fichier ouvert par un éditeur en dehors de l'environnement de développement intégré.  Le message vous permet de recharger le fichier de stockage.  
  
 **Charger automatiquement les modifications, si elles ont été enregistrées**  
 Lorsque l'option **Détecter quand le fichier est modifié en dehors de l'environnement** est sélectionnée et que des modifications sont apportées à un fichier ouvert dans l'IDE en dehors de cet environnement, un message d'avertissement est généré par défaut.  Lorsque cette option est sélectionnée, aucun message d'avertissement ne s'affiche et le document est rechargé dans l'IDE pour relever les modifications externes.  
  
 **Autoriser la modification des fichiers en lecture seule, avertir à l'enregistrement**  
 Lorsque cette option est activée, vous pouvez ouvrir et modifier un fichier en lecture seule.  Lorsque vous avez terminé, vous devez utiliser le  **Enregistrer sous**commande pour enregistrer le fichier sous un nouveau nom si vous souhaitez conserver un enregistrement de vos modifications.  
  
 **Ouvrir un fichier à l'aide du répertoire du document actif**  
 Lorsque cette option est activée, la boîte de dialogue **Ouvrir un fichier** affiche le répertoire du document actif.  Lorsque cette option est désactivée, la boîte de dialogue **Ouvrir un fichier** affiche le répertoire utilisé la dernière fois pour ouvrir un fichier.  
  
 **Vérifier la cohérence des fins de ligne au chargement**  
 Sélectionnez cette option pour que l'éditeur numérise les fins de ligne dans un fichier et affiche un message en cas si des incohérences sont détectées dans la mise en forme des fins de ligne.  
  
 **Afficher un avertissement lorsqu'une annulation globale affecte des fichiers modifiés**  
 Sélectionnez cette option pour afficher un message lorsque la commande **Annulation globale** restaure les modifications de refactorisation effectuées dans les fichiers qui ont également été changés après l'opération de refactorisation.  Le fait de rétablir un fichier à son état de pré\-refactorisation peut ignorer les modifications apportées ultérieurement au fichier.  
  
 **Afficher les fichiers divers dans l'Explorateur de solutions**  
 Sélectionnez cette option pour afficher le nœud **Fichiers divers** dans l'**Explorateur de solutions**.  Les fichiers divers sont des fichiers qui ne sont pas associés à un projet ou une solution, mais qui apparaissent dans l'**Explorateur de solutions** pour vous faciliter le travail.  
  
> [!NOTE]
>  Sélectionnez cette option pour activer la commande **Afficher dans le navigateur** du menu **Fichier** pour les documents Web non inclus dans l'application Web active.  
  
 **\<** *n* **\>  éléments enregistrés dans le projet Fichiers divers**  
 Spécifie le nombre de fichiers à rendre persistants dans le dossier **Fichiers divers** de l'**Explorateur de solutions**.  Ces fichiers sont répertoriés même s'ils ne sont plus ouverts dans un éditeur.  Vous pouvez spécifier tout nombre entier de 0 à 256.  Le nombre par défaut est 0.  
  
 Par exemple, si vous affectez à cette option la valeur 5 et que vous avez ouvert 10 fichiers divers, lorsque vous fermez les 10 fichiers, les 5 premiers resteront affichés dans le dossier **Fichiers divers**.  
  
 **Enregistrer les documents au format Unicode lorsque les données ne peuvent pas être enregistrées dans la page de codes**  
 Sélectionnez cette option pour que les fichiers qui contiennent des informations incompatibles avec la page de codes sélectionnée soient enregistrés en Unicode par défaut.  
  
## Voir aussi  
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)   
 [Fichiers divers](../../ide/reference/miscellaneous-files.md)   
 [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md)