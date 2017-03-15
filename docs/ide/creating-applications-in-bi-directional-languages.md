---
title: "Cr&#233;ation d&#39;applications en langues bidirectionnelles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langue arabe, créer des applications"
  - "prise en charge des langues bidirectionnelles, à propos de la prise en charge des langues bidirectionnelles"
  - "affichage de caractères hébreux, créer des applications"
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Cr&#233;ation d&#39;applications en langues bidirectionnelles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser Visual Studio pour créer des applications qui affichent correctement le texte dans des langues écrites de droite à gauche, notamment l'arabe et l'hébreu.  Pour certaines fonctionnalités, il vous suffit de définir les propriétés.  Pour d'autres, il vous faut les implémenter dans le code.  
  
> [!NOTE]
>  Pour entrer et afficher des langues bidirectionnelles, vous devez utiliser une version de Windows configurée avec la langue appropriée.  Il peut s'agir d'une version anglaise de Windows disposant du module de prise en charge linguistique approprié ou de la version localisée de Windows appropriée.  
  
## Types de l'application des langues bidirectionnelles de ce support  
  
1.  Applications Windows.  Vous pouvez créer des applications entièrement bidirectionnelles prenant en charge le texte bidirectionnel, l'ordre de lecture de droite à gauche et l'effet miroir \(inversement de la disposition des fenêtres, menus, boîtes de dialogue, etc.\).  À l'exception de l'effet miroir, ces fonctionnalités sont disponibles par défaut ou en tant que paramètres de propriété.  L'effet miroir est pris en charge par nature pour certaines fonctionnalités, telles que les boîtes de message.  Toutefois, dans d'autres cas, il vous faut l'implémenter dans le code.  Pour plus d'informations, consultez [Prise en charge bidirectionnelle pour les applications Windows Forms](../Topic/Bi-Directional%20Support%20for%20Windows%20Forms%20Applications.md).  
  
2.  Applications Web.  Prise en charge des services Web et réception envoyant UTF\-8 et le texte Unicode, ce appropriés pour les applications impliquant des langues bidirectionnelles.  Les applications clientes Web dépend des navigateurs pour leur interface utilisateur, le degré de prise en charge bidirectionnelle dans une application Web dépend à quel point prend en charge de navigateur ces fonctionnalités bidirectionnelles.  Dans Visual Studio, vous pouvez créer des applications avec une prise en charge du texte en arabe ou en hébreu, de l'ordre de lecture de droite à gauche, de l'encodage des fichiers et des paramètres de culture locale.  Pour plus d'informations, consultez [Bidirectional Support for ASP.NET Web Applications](../Topic/Bidirectional%20Support%20for%20ASP.NET%20Web%20Applications.md).  
  
3.  Les applications consoles.  Les applications console n'offrent pas de prise en charge de texte pour les langues bidirectionnelles.  C'est la façon dont les fenêtres fonctionne avec les applications console.  
  
## Fonctionnalités Visual Studio entièrement prises en charge  
 Au moment du design dans Visual Studio, vous pouvez utiliser les langues bidirectionnelles des manières décrites ci\-dessous.  
  
-   **Entrée de texte** Visual Studio prend en charge Unicode. Ainsi, si votre système est configuré avec les paramètres régionaux et la langue d'entrée appropriés, vous pouvez entrer du texte en arabe ou en hébreu. \(La prise en charge de l'arabe comprend les signes Kashidé et diacritiques.\)  
  
-   **Noms d'objets** Vous pouvez utiliser les langues bidirectionnelles pour assigner des noms aux solutions, projets, fichiers, dossiers, etc.  Dans le code, vous pouvez utiliser les langues bidirectionnelles pour les noms de variables, classes, objets, attributs, métadonnées, etc.  
  
-   **Codage de fichiers** Vous pouvez enregistrer et ouvrir des fichiers avec un encodage spécifique à la langue ou Unicode.  Pour plus d'informations, consultez [Comment : enregistrer et ouvrir des fichiers avec encodage](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## Fonctionnalités partiellement ou non prises en charge  
 D'autres fonctionnalités communes aux applications en langue bidirectionnelle sont seulement partiellement, voire pas du tout, prises en charge.  Ces niveaux sont les suivants :  
  
-   **Ordre de lecture de droite à gauche** Par défaut, dans Visual Studio, les contrôles d'entrée de texte utilisent un ordre de lecture de gauche à droite.  Dans la plupart des cas, vous pouvez utiliser les commandes Windows standard pour modifier l'ordre de lecture.  Par exemple, vous pouvez utiliser la combinaison de touches Ctrl\+Maj droite pour modifier la fenêtre Propriétés afin de permettre la prise en charge de l'ordre de lecture de droite à gauche pour les valeurs de propriété.  
  
     Cet ordre de lecture n'est cependant pas pris en charge partout dans Visual Studio.  Parmi les exceptions :  
  
    -   Les cases à cocher, listes déroulantes et d'autres contrôles des boîtes de dialogue Visual Studio utilisent toujours l'ordre de lecture de gauche à droite.  
  
    -   L'éditeur de code \(et éditeur de texte\) ne prend pas en charge l'ordre de lecture de droite à gauche.  Vous pouvez entrer du texte en langue bidirectionnelle, mais l'ordre de lecture reste de gauche à droite.  
  
## Attribution d'un nom à des éléments à l'aide de texte en arabe ou en hébreu  
 Vous pouvez utiliser du texte en arabe ou en hébreu pour assigner des noms aux dossiers, variables, etc.  En arabe, vous pouvez utiliser tout caractère arabique, y compris les signes Kashidé et diacritiques.  
  
 Les éléments ci\-dessous peuvent être nommés à l'aide de texte en arabe ou en hébreu et être gérés correctement dans Visual Studio.  
  
-   Solutions, projets et fichiers, ainsi que tout dossier compris dans le chemin d'accès au projet.  L'Explorateur de solutions affiche alors correctement le nom de la solution et de l'élément.  
  
-   Contenu de fichier.  Vous pouvez ouvrir ou enregistrer des fichiers avec un encodage Unicode ou une page de code sélectionnée.  
  
    > [!NOTE]
    >  L'éditeur de code représente un cas particulier.  Pour plus d'informations, reportez\-vous au passage correspondant ci\-dessous.  
  
-   Éléments de données.  L'**Explorateur de serveurs** affiche correctement ces éléments et vous permet de les modifier.  
  
-   Éléments copiés dans le Presse\-papiers de Windows.  
  
-   Attributs et métadonnées.  
  
-   Valeurs de propriété.  Vous pouvez utiliser du texte en arabe ou en hébreu dans la fenêtre Propriétés.  Cette fenêtre vous permet de basculer entre l'ordre de lecture de droite à gauche et de gauche à droite à l'aide des séquences de touches Windows standard \(CTRLl\+Maj droite pour l'ordre de lecture de droite à gauche, CTRL\+Maj gauche pour l'ordre de lecture de gauche à droite\).  
  
-   Code et texte littéral.  Dans l'éditeur de code \(qui est également l'éditeur de texte\), vous pouvez utiliser l'arabe ou l'hébreu pour nommer des classes, fonctions, variables, propriétés, littéraux de chaîne, attributs, etc.  Toutefois, l'éditeur ne prend pas en charge l'ordre de lecture de droite à gauche : le texte part toujours de la marge gauche.  
  
    > [!TIP]
    >  Placez les littéraux de chaîne dans des fichiers de ressources plutôt que de les coder de manière irréversible dans vos programmes.  Pour plus d'informations, consultez [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/fr-fr/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
    > [!NOTE]
    >  Vous devez rester cohérent dans votre manière de faire référence aux objets nommés dans ces langues.  Par exemple, si vous utilisez des signes Kashidé pour nommer une variable en arabe, veillez à toujours utiliser des signes Kashidé lorsque vous y faites référence, sinon des erreurs se produiront.  
  
-   Commentaires de code.  Vous pouvez créer des commentaires de code en arabe ou en hébreu.  Vous pouvez également utiliser ces langues dans l'outil de génération de commentaires.  
  
## Voir aussi  
 [Prise en charge bidirectionnelle pour les applications Windows Forms](../Topic/Bi-Directional%20Support%20for%20Windows%20Forms%20Applications.md)   
 [Bidirectional Support for ASP.NET Web Applications](../Topic/Bidirectional%20Support%20for%20ASP.NET%20Web%20Applications.md)   
 [Globalisation d'applications](../ide/globalizing-applications.md)   
 [Localisation d'applications](../ide/localizing-applications.md)