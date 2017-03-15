---
title: "Partage de classes entre plusieurs DSL &#224; l&#39;aide d&#39;une biblioth&#232;que DSL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 7
---
# Partage de classes entre plusieurs DSL &#224; l&#39;aide d&#39;une biblioth&#232;que DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Kit de développement logiciel de visualisation et de modélisation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , vous pouvez créer une définition incomplète DÉSOLÉ que vous pouvez importer dans un autre langage spécifique à un domaine.  Cela vous permet d'isoler les parties communes de modèles semblables.  
  
## Création et utilisation de bibliothèques DÉSOLÉ  
  
#### Pour créer une bibliothèque DÉSOLÉ  
  
1.  Créez un nouveau projet DÉSOLÉ, puis choisissez le modèle de solution de bibliothèque DÉSOLÉ.  
  
     Un projet unique DÉSOLÉ est créé avec un modèle vide.  
  
2.  Vous pouvez ajouter des classes de domaine, les relations, formes et ainsi de suite.  
  
     Les éléments contenus dans la bibliothèque ne doivent pas former une arborescence unique d'incorporation.  
  
     Pour définir une relation que les importateurs peuvent utiliser, créez deux classes de domaine et créer la relation entre eux.  
  
     envisagez de définir **modificateur d'héritage** des classes de domaine à `Abstract`.  
  
3.  Vous pouvez ajouter les éléments que vous définissez dans l'explorateur DÉSOLÉ, tel que les générateurs de connexion.  
  
4.  Vous pouvez ajouter ces personnalisations qui requièrent code supplémentaires, telles que les contraintes de validation.  
  
5.  cliquez sur **Transformer tous les modèles**.  
  
6.  Générez le projet.  
  
7.  Lorsque vous distribuez du langage DÉSOLÉ pour que d'autres personnes utilisent, vous devez fournir l'assembly compilé \(DLL\) et le fichier `DslDefinition.dsl`.  vous pouvez rechercher l'assembly compilé dans un dossier sous `Dsl\bin\*`  
  
#### Pour importer une bibliothèque DÉSOLÉ  
  
1.  Dans une autre définition DÉSOLÉ, dans **Explorateur DÉSOLÉ**, cliquez avec le bouton droit sur la classe racine du langage DÉSOLÉ, puis cliquez sur **ajoutez la nouvelle importation de DslLibrary**.  
  
2.  Dans la fenêtre Propriétés, affectez **chemin d'accès de fichier** de la bibliothèque.  Vous pouvez utiliser un chemin d'accès absolu.  
  
     La bibliothèque importée s'affiche dans l'explorateur DÉSOLÉ, en mode lecture seule.  
  
3.  Vous pouvez utiliser les classes importées comme des classes de base.  Créez une classe de domaine dans du code DÉSOLÉ important, et dans la fenêtre Propriétés, affectez **classe de base** à une classe importée.  
  
4.  transformation de clic tous les modèles.  
  
5.  Ajoutez au projet DÉSOLÉ une référence à l'assembly \(DLL\) qui a été généré par le projet de bibliothèque DÉSOLÉ.  
  
6.  Générez la solution.  
  
 Une bibliothèque DÉSOLÉ peut importer d'autres bibliothèques.  Lorsque vous importez une bibliothèque, ses importations s'affichent automatiquement dans l'explorateur DÉSOLÉ.  
  
## Voir aussi  
 [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)