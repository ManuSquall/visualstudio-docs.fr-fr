---
title: "Création d’applications en langues bidirectionnelles | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: db7afbc68ab4e02803959dd0ff0b4de92233fece
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-applications-in-bi-directional-languages"></a>Création d'applications en langues bidirectionnelles
Vous pouvez utiliser Visual Studio pour créer des applications qui affichent correctement les langues qui s’écrivent de droite à gauche, comme l’arabe et l’hébreu. Pour certaines fonctionnalités, il suffit de définir des propriétés. Dans d’autres cas, vous devez implémenter des fonctionnalités dans le code.  
  
> [!NOTE]
>  Pour entrer et afficher des langues bidirectionnelles, vous devez utiliser une version de Windows configurée avec la langue appropriée. Il peut s’agir d’une version anglaise de Windows sur laquelle est installé le module linguistique correspondant, ou d’une version localisée de Windows.  
  
## <a name="types-of-application-that-support-bi-directional-languages"></a>Types d’applications qui prennent en charge les langues bidirectionnelles  
  
1.  Applications Windows. Vous pouvez créer des applications entièrement bidirectionnelles prenant en charge le texte bidirectionnel, l’ordre de lecture de droite à gauche et la mise en miroir (c’est-à-dire l’inversement de la disposition des fenêtres, des menus, des boîtes de dialogue, etc.). À l’exception de la mise en miroir, ces fonctionnalités sont disponibles par défaut ou en tant que paramètres de propriété. La mise en miroir est prise en charge par défaut pour certaines fonctionnalités, telles que les boîtes de message. Dans d’autres cas, vous devez implémenter la mise en miroir dans votre code. Pour plus d’informations, consultez [Prise en charge bidirectionnelle pour les applications Windows Forms](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2).  
  
2.  Applications web. Les services web prennent en charge l’envoi et la réception de texte UTF-8 et Unicode. Ils sont donc adaptés aux applications qui impliquent des langues bidirectionnelles. Les applications web clientes s’appuient sur les navigateurs pour leur interface utilisateur. Le degré de prise en charge bidirectionnelle d’une application web dépend donc du degré de prise en charge du navigateur. Dans Visual Studio, vous pouvez créer des applications avec prise en charge de l’arabe ou de l’hébreu, de l’ordre de lecture de droite à gauche, de l’encodage des fichiers et des paramètres de culture locale. Pour plus d’informations, consultez [Prise en charge bidirectionnelle pour les applications web ASP.NET](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).  
  
3.  Les applications consoles. Les applications console ne prennent pas en charge le texte en langue bidirectionnelle. Cela est dû à la façon dont Windows fonctionne avec les applications console.  
  
## <a name="visual-studio-features-that-are-fully-supported"></a>Fonctionnalités de Visual Studio qui sont entièrement prises en charge  
 Dans Visual Studio, au moment du design, vous pouvez utiliser les langues bidirectionnelles des façons suivantes :  
  
-   **Saisie de texte** Visual Studio prend en charge le format Unicode. Par conséquent, si votre système est configuré d’après les paramètres régionaux et la langue d’entrée souhaités, vous pouvez saisir du texte en arabe ou en hébreu (la prise en charge de l’arabe comprend les signes kachidé et les signes diacritiques).  
  
-   **Noms d’objets** Vous pouvez utiliser les langues bidirectionnelles pour attribuer des noms aux solutions, projets, fichiers, dossiers, etc. Dans le code, vous pouvez utiliser les langues bidirectionnelles pour les noms de variables, de classes, d’objets, d’attributs, de métadonnées et d’autres éléments.  
  
-   **Encodage des fichiers** Vous pouvez enregistrer et ouvrir des fichiers avec un encodage Unicode ou spécifique à une langue. Pour plus d’informations, consultez [Guide pratique pour enregistrer et ouvrir des fichiers avec encodage](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## <a name="features-with-limited-or-no-support"></a>Fonctionnalités avec prise en charge limitée et fonctionnalités non prises en charge  
 Certaines fonctionnalités courantes des applications pour langues bidirectionnelles ne sont pas entièrement prises en charge par Visual Studio, voire pas du tout. Elles incluent notamment :  
  
-   **Ordre de lecture de droite à gauche** Par défaut, les contrôles de saisie de texte que vous utilisez dans Visual Studio utilisent l’ordre de lecture de gauche à droite. Dans la plupart des cas, vous pouvez utiliser des méthodes Windows standard pour changer l’ordre de lecture. Par exemple, vous pouvez appuyer sur Ctrl+Maj droite pour que la fenêtre Propriétés prenne en charge l’ordre de lecture de droite à gauche.  
  
     Cependant, l’ordre de lecture de droite à gauche n’est pas pris en charge partout dans Visual Studio. Voici certaines exceptions :  
  
    -   Les cases à cocher, listes déroulantes et autres contrôles des boîtes de dialogue Visual Studio utilisent toujours l’ordre de lecture de gauche à droite.  
  
    -   L’éditeur de code (et éditeur de texte) ne prend pas en charge l’ordre de lecture de droite à gauche. Vous pouvez entrer du texte dans une langue bidirectionnelle, mais l’ordre de lecture restera de gauche à droite.  
  
## <a name="naming-things-using-arabic-or-hebrew-text"></a>Attributions de noms avec du texte en arabe ou en hébreu  
 Vous pouvez utiliser du texte en arabe ou en hébreu pour attribuer des noms aux dossiers, variables ou autres objets. Quand vous utilisez l’arabe, vous pouvez utiliser les caractères arabes, y compris les signes kachidé et les signes diacritiques.  
  
 Les éléments suivants peuvent être nommés en arabe et en hébreu, et sont gérés correctement par Visual Studio :  
  
-   Les noms de solutions, de projets et de fichiers, y compris les dossiers que vous incluez dans le chemin du projet. L’Explorateur de solutions affiche les noms d’éléments et de solutions correctement.  
  
-   Contenu des fichiers. Vous pouvez ouvrir ou enregistrer des fichiers avec encodage Unicode ou avec une page de code sélectionnée.  
  
    > [!NOTE]
    >  L’éditeur de code est un cas particulier. Pour plus de détails, voir ci-dessous.  
  
-   Éléments de données. L’**Explorateur de serveurs** affiche correctement ces éléments et vous permet de les modifier.  
  
-   Éléments copiés dans le Presse-papiers Windows.  
  
-   Attributs et métadonnées.  
  
-   Valeurs de propriétés. Vous pouvez utiliser l’arabe ou l’hébreu texte dans la fenêtre Propriétés. La fenêtre vous permet de basculer entre l’ordre de lecture de droite à gauche et celui de gauche à droite à l’aide de séquences de touches Windows standard (CTRL + Maj droite pour l’ordre de droite à gauche, et CTRL + Maj gauche pour l’ordre de gauche à droite).  
  
-   Code et texte littéral. Dans l’éditeur de code (qui est également l’éditeur de texte), vous pouvez utiliser l’arabe ou l’hébreu pour nommer des classes, des fonctions, des variables, des propriétés, des littéraux de chaîne, des attributs; etc. Toutefois, l’éditeur ne prend pas en charge l’ordre de lecture de droite à gauche et le texte commence toujours à la marge de gauche.  
  
    > [!TIP]
    >  Il est recommandé de placer des littéraux de chaîne dans les fichiers de ressources au lieu de les coder en dur dans vos programmes. Pour plus d’informations, consultez [Procédure pas à pas : localisation de Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
    > [!NOTE]
    >  Vous devez être cohérent dans la façon dont vous faites référence aux objets nommés dans ces langues. Par exemple, si vous utilisez des signes kachidé pour nommer une variable en arabe, vous devrez toujours utiliser des signes kachidé dans vos références à cette variable, sinon une erreur se produira.  
  
-   Commentaires de code. Vous pouvez créer des commentaires en arabe ou en hébreu. Vous pouvez également utiliser ces langues dans le générateur de commentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge bidirectionnelle pour les applications Windows Forms](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2)   
 [Prise en charge bidirectionnelle pour les applications web ASP.NET](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)   
 [Globalisation d’applications](../ide/globalizing-applications.md)   
 [Localisation d’applications](../ide/localizing-applications.md)