---
title: Prise en charge de l’arabe et de l’hébreu
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57bccfccb77c5a80fd2630680564f88f08d7ca5b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591994"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Prise en charge des langues bidirectionnelles dans Visual Studio

Visual Studio peut afficher correctement du texte en arabe et en hébreu, et il vous permet d’entrer du texte bidirectionnel pour les noms et les valeurs des objets.

> [!NOTE]
> Pour entrer et afficher des langues bidirectionnelles, vous devez utiliser une version de Windows configurée avec la langue appropriée. Il peut s’agir d’une version anglaise de Windows sur laquelle est installé le module linguistique correspondant, ou d’une version localisée de Windows.

## <a name="fully-supported-features"></a>Fonctionnalités entièrement prises en charge

Au moment du design dans Visual Studio, vous pouvez utiliser des langues bidirectionnelles lors de la saisie de texte, du nommage des objets, et lors de l’enregistrement et de l’ouverture des fichiers.

### <a name="text-entry"></a>Entrée de texte

Visual Studio prend en charge le format Unicode. Par conséquent, si votre système est configuré d’après les paramètres régionaux et la langue d’entrée souhaités, vous pouvez entrer du texte en arabe ou en hébreu (la prise en charge de l’arabe comprend les signes kachidé et les signes diacritiques).

### <a name="arabic-or-hebrew-object-names"></a>Noms d’objets en arabe ou en hébreu

Vous pouvez utiliser les langues bidirectionnelles pour affecter des noms aux solutions, projets, fichiers, dossiers, etc. Dans le code, vous pouvez utiliser les langues bidirectionnelles pour les noms de variables, de classes, d’objets, d’attributs, de métadonnées et d’autres éléments. Quand vous utilisez l’arabe, vous pouvez utiliser les caractères arabes, y compris les signes kachidé et les signes diacritiques.

Les éléments suivants peuvent être nommés en arabe et en hébreu, et sont gérés correctement par Visual Studio :

- Les noms de solutions, de projets et de fichiers, y compris les dossiers que vous incluez dans le chemin du projet.

   L’**Explorateur de solutions** affiche correctement les noms de solutions et d’éléments.

- Contenu des fichiers.

   Vous pouvez ouvrir ou enregistrer des fichiers avec encodage Unicode ou avec une page de code sélectionnée.

- Éléments de données.

   L’**Explorateur de serveurs** affiche correctement ces éléments et vous pouvez les modifier.

- Éléments copiés dans le Presse-papiers Windows.

- Attributs et métadonnées.

- Valeurs de propriétés.

   Vous pouvez utiliser du texte en arabe ou en hébreu dans la fenêtre **Propriétés**. Elle permet de basculer entre l’ordre de lecture de droite à gauche et celui de gauche à droite en utilisant des séquences de touches Windows standard (**Ctrl**+**Maj droite** pour l’ordre de droite à gauche et **Ctrl**+**Maj gauche** pour l’ordre de gauche à droite).

- Code et texte littéral.

   Dans l’éditeur de code, vous pouvez utiliser l’arabe ou l’hébreu pour nommer des classes, des fonctions, des variables, des propriétés, des littéraux de chaîne, des attributs, etc. Toutefois, l’éditeur ne prend pas en charge l’ordre de lecture de droite à gauche et le texte commence toujours à la marge de gauche.

   > [!TIP]
   > Vous devez placer des littéraux de chaîne dans les fichiers de ressources au lieu de les coder en dur dans vos programmes. Pour plus d’informations, consultez [Ressources dans les applications de bureau (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Vous devez être cohérent dans votre façon de faire référence aux objets nommés en arabe et en hébreu. Par exemple, si vous utilisez des signes kachidé pour nommer une variable en arabe, vous devez toujours utiliser des signes kachidé dans vos références à cette variable, sinon une erreur se produit.

- Commentaires de code. Vous pouvez créer des commentaires en arabe ou en hébreu. Vous pouvez également utiliser ces langues dans le générateur de commentaires.

### <a name="file-encoding"></a>Encodage des fichiers

Vous pouvez enregistrer et ouvrir des fichiers avec un encodage Unicode ou spécifique à une langue. Pour plus d’informations, consultez la page [Guide pratique pour enregistrer et ouvrir des fichiers avec encodage](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Ordre de lecture de droite à gauche

Visual Studio a une prise en charge limitée de l’ordre de lecture de droite à gauche. Par défaut, les contrôles de d’entrée de texte dans Visual Studio utilisent l’ordre de lecture de gauche à droite. Dans la plupart des cas, vous pouvez utiliser des méthodes Windows standard pour changer l’ordre de lecture. Par exemple, vous pouvez appuyer sur **Ctrl**+**Maj droite** pour que la fenêtre **Propriétés** gère l’ordre de lecture de droite à gauche pour les valeurs de propriété.

L’ordre de lecture de droite à gauche n’est pas pris en charge aux endroits suivants dans Visual Studio :

- Les cases à cocher, listes déroulantes et autres contrôles des boîtes de dialogue Visual Studio utilisent toujours l’ordre de lecture de gauche à droite.

- L’éditeur de code (et éditeur de texte) ne prend pas en charge l’ordre de lecture de droite à gauche. Vous pouvez entrer du texte dans une langue bidirectionnelle, mais l’ordre de lecture reste de gauche à droite.

## <a name="see-also"></a>Voir aussi

- [Développer des applications mondialisées et localisées](globalizing-and-localizing-applications.md)
