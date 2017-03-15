---
title: "Propri&#233;t&#233;s des fichiers, JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.expandedsdknode.fileversion"
  - "javascript.project.property.expandedsdknode.uri"
  - "javascript.project.property.expandedsdknode.filename"
  - "javascript.project.property.reference.description"
  - "javascript.project.property.reference.specificversion"
  - "javascript.project.property.reference.identity"
  - "javascript.project.property.fullpath"
  - "javascript.project.property.packageaction"
  - "javascript.project.property.reference.package"
  - "javascript.project.property.copytooutputdirectory"
  - "javascript.project.property.expandedsdknode.sdkpath"
  - "javascript.project.property.reference.filetype"
  - "javascript.project.property.reference.culture"
  - "javascript.project.property.filename"
  - "javascript.project.property.reference.resolvedpath"
  - "javascript.project.property.reference.version"
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Propri&#233;t&#233;s des fichiers, JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser les propriétés des fichiers pour indiquer les actions que le système de projet doit effectuer sur les fichiers.  Par exemple, vous pouvez définir des propriétés de fichier pour indiquer si un fichier doit être ajouté au package en tant que fichier de ressources.  
  
 Vous pouvez sélectionner n'importe quel fichier dans l'Explorateur de solutions, puis examiner ses propriétés dans la fenêtre Propriétés.  Les fichiers JavaScript ont quatre propriétés : **Copier dans le répertoire de sortie**, **action de module**, **Nom de fichier**, et **chemin d'accès de fichier**.  
  
## Propriétés des fichiers  
 Cette section décrit les propriétés communes aux fichiers JavaScript.  
  
### Propriété Copier dans le répertoire de sortie  
 Cette propriété spécifie les conditions dans lesquelles le fichier source sélectionné sera copié dans le répertoire de sortie.  Sélectionnez **Ne pas copier** si le fichier ne sera jamais copié vers le répertoire de sortie.  Sélectionnez **Toujours copier** si le fichier sera toujours copié vers le répertoire de sortie.  Sélectionnez **Copier si plus récent** si le fichier sera copié uniquement lorsqu'il est plus récent qu'un fichier existant du même nom dans le répertoire de sortie.  
  
### Action de module  
 La propriété **action de module** indique que Visual Studio effectue avec un fichier lorsqu'une génération.  **action de module** peut avoir l'une des différentes valeurs :  
  
-   **aucun** \- Le fichier n'est pas inclus dans le manifeste du package.  Il peut s'agir d'un fichier texte contenant de la documentation, par exemple un fichier Readme.  
  
-   **Contenu** \- Le fichier est inclus dans le manifeste du package.  Par exemple, cette configuration est la valeur par défaut de .htm, un fichier .js, un .css, une image, un son, ou un fichier vidéo.  
  
-   **manifeste** – Le fichier n'est pas inclus dans le manifeste du package.  À la place, le fichier est utilisé pour les entrées lors de la génération du manifeste du package.  Valeur par défaut pour le fichier de package.appxmanifest.  
  
-   **ressource** \- Le fichier n'est pas inclus dans le manifeste du package.  À la place, le contenu du fichier est indexé dans l'index \(PRI\) de ressource de package qui entre dans le manifeste du package.  Cette valeur est utilisée en général pour les fichiers de ressources.  
  
 La valeur par défaut pour **action de module** dépend de l'extension du fichier que vous ajoutez à la solution.  
  
### Propriété Nom de fichier  
 Affiche le nom de fichier comme valeur en lecture seule.  Pour renommer le fichier, vous devez cliquer avec le bouton droit dans l'explorateur de solutions et sélectionnez **Renommer**.  
  
### Propriété de chemin d'accès complet  
 Affiche le chemin d'accès complet au fichier en tant que valeur en lecture seule.  Pour modifier le chemin d'accès du fichier, vous pouvez glisser\-déplacer l'explorateur de solutions.  
  
## Propriétés de fichier de référence  
 Cette section décrit les propriétés communes aux fichiers référencés d' [!INCLUDE[win8_app_js](../../ide/reference/includes/win8_app_js_md.md)].  Lorsque vous sélectionnez une référence telle qu'un fichier de .winmd, une référence du Kit de développement logiciel, une référence entre projets, ou un explorateur de référence d'assembly de solution, d'autres propriétés peuvent afficher dans la fenêtre Propriétés, selon le type de fichier.  
  
### Culture  
 Affiche le langage associé à la référence.  
  
### Type de fichier  
 Affiche le type de fichier de la référence.  
  
### Version de fichier  
 Affiche la version du fichier de référence.  
  
### Identité  
 Affiche l'identité de la référence utilisée dans le projet, qui est stocké dans le fichier projet.  
  
### Package  
 Affiche le nom du manifeste du package associé à la référence.  
  
### Chemin résolu  
 Affiche le chemin d'accès de la référence utilisée dans le projet.  
  
### Chemin d'accès du Kit de développement logiciel  
 Affiche le chemin d'accès au fichier référencé du Kit de développement logiciel.  
  
### Uri  
 Affiche l'URI qui doit être inclus dans le HTML du projet ou les fichiers JavaScript pour inclure le fichier en tant que fichier source.  
  
### Version  
 Affiche la version de la référence.  
  
## Voir aussi  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)