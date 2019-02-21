---
title: Prise en charge pour les applications en arabe et en hébreu
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aa75ee12e09d4aa56a112a135a2e9e913b5cd39
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335231"
---
# <a name="create-applications-in-bi-directional-languages"></a>Créer des applications dans des langues bidirectionnelles

Vous pouvez utiliser Visual Studio pour créer des applications qui affichent correctement les langues qui s’écrivent de droite à gauche, comme l’arabe et l’hébreu. Pour certaines fonctionnalités, il suffit de définir des propriétés. Dans d’autres cas, vous devez implémenter des fonctionnalités dans le code.

> [!NOTE]
> Pour entrer et afficher des langues bidirectionnelles, vous devez utiliser une version de Windows configurée avec la langue appropriée. Il peut s’agir d’une version anglaise de Windows sur laquelle est installé le module linguistique correspondant, ou d’une version localisée de Windows.

## <a name="types-of-applications-that-support-bi-directional-languages"></a>Types d’applications qui prennent en charge les langues bidirectionnelles

-  Applications Windows

   Vous pouvez créer des applications entièrement bidirectionnelles prenant en charge le texte bidirectionnel, l’ordre de lecture de droite à gauche et la mise en miroir (c’est-à-dire l’inversement de la disposition des fenêtres, des menus, des boîtes de dialogue, etc.). À l’exception de la mise en miroir, ces fonctionnalités sont disponibles par défaut ou en tant que paramètres de propriété. La mise en miroir est prise en charge par défaut pour certaines fonctionnalités, telles que les boîtes de message. Dans d’autres cas, vous devez implémenter la mise en miroir dans votre code. Pour plus d’informations, consultez la page [Prise en charge bidirectionnelle pour les applications Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

-  Applications web

   Les services web prennent en charge l’envoi et la réception de texte UTF-8 et Unicode. Ils sont donc adaptés aux applications qui comportent des langues bidirectionnelles. Les applications clientes web s’appuient sur les navigateurs pour leur interface utilisateur. Le degré de prise en charge bidirectionnelle d’une application web dépend donc de celui du navigateur du client. Dans Visual Studio, vous pouvez créer des applications avec prise en charge de l’arabe ou de l’hébreu, de l’ordre de lecture de droite à gauche, de l’encodage des fichiers et des paramètres de culture locale. Pour plus d’informations, consultez la page [Prise en charge bidirectionnelle pour les applications web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

Les applications console ne prennent pas en charge le texte en langue bidirectionnelle. Cela est dû à la façon dont Windows fonctionne avec les applications console.

## <a name="fully-supported-features"></a>Fonctionnalités entièrement prises en charge

Dans Visual Studio, au moment du design, vous pouvez utiliser les langues bidirectionnelles des façons suivantes :

- **Entrée de texte**

   Visual Studio prend en charge le format Unicode. Par conséquent, si votre système est configuré d’après les paramètres régionaux et la langue d’entrée souhaités, vous pouvez entrer du texte en arabe ou en hébreu (la prise en charge de l’arabe comprend les signes kachidé et les signes diacritiques).

- **Noms d’objets**

   Vous pouvez utiliser les langues bidirectionnelles pour attribuer des noms aux solutions, projets, fichiers, dossiers, etc. Dans le code, vous pouvez utiliser les langues bidirectionnelles pour les noms de variables, de classes, d’objets, d’attributs, de métadonnées et d’autres éléments.

- **Encodage de fichiers**

   Vous pouvez enregistrer et ouvrir des fichiers avec un encodage Unicode ou spécifique à une langue. Pour plus d'informations, voir [Procédure : Enregistrer et ouvrir des fichiers avec encodage](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-support"></a>Fonctionnalités avec prise en charge limitée

### <a name="right-to-left-reading-order"></a>Ordre de lecture de droite à gauche

Par défaut, les contrôles de d’entrée de texte dans Visual Studio utilisent l’ordre de lecture de gauche à droite. Dans la plupart des cas, vous pouvez utiliser des méthodes Windows standard pour changer l’ordre de lecture. Par exemple, vous pouvez appuyer sur **Ctrl**+**Maj droite** pour que la fenêtre **Propriétés** gère l’ordre de lecture de droite à gauche pour les valeurs de propriété. Cependant, l’ordre de lecture de droite à gauche n’est pas pris en charge partout dans Visual Studio :

- Les cases à cocher, listes déroulantes et autres contrôles des boîtes de dialogue Visual Studio utilisent toujours l’ordre de lecture de gauche à droite.

- L’éditeur de code (et éditeur de texte) ne prend pas en charge l’ordre de lecture de droite à gauche. Vous pouvez entrer du texte dans une langue bidirectionnelle, mais l’ordre de lecture restera de gauche à droite.

## <a name="arabic-or-hebrew-object-names"></a>Noms d’objets en arabe ou en hébreu

Vous pouvez utiliser du texte en arabe ou en hébreu pour attribuer des noms aux dossiers, variables ou autres objets. Quand vous utilisez l’arabe, vous pouvez utiliser les caractères arabes, y compris les signes kachidé et les signes diacritiques.

Les éléments suivants peuvent être nommés en arabe et en hébreu et sont gérés correctement par Visual Studio :

- Les noms de solutions, de projets et de fichiers, y compris les dossiers que vous incluez dans le chemin du projet. L’**Explorateur de solutions** affiche correctement les noms de solutions et d’éléments.

- Contenu des fichiers. Vous pouvez ouvrir ou enregistrer des fichiers avec encodage Unicode ou avec une page de code sélectionnée.

    > [!NOTE]
    > L’éditeur de code ne prend pas en charge l’ordre de lecture de droite à gauche.

- Éléments de données. L’**Explorateur de serveurs** affiche correctement ces éléments et vous permet de les modifier.

- Éléments copiés dans le Presse-papiers Windows.

- Attributs et métadonnées.

- Valeurs de propriétés. Vous pouvez utiliser du texte en arabe ou en hébreu dans la fenêtre **Propriétés**. Elle permet de basculer entre l’ordre de lecture de droite à gauche et celui de gauche à droite en utilisant des séquences de touches Windows standard (**Ctrl**+**Maj droite** pour l’ordre de droite à gauche et **Ctrl**+**Maj gauche** pour l’ordre de gauche à droite).

- Code et texte littéral. Dans l’éditeur de code, vous pouvez utiliser l’arabe ou l’hébreu pour nommer des classes, des fonctions, des variables, des propriétés, des littéraux de chaîne, des attributs, etc. Toutefois, l’éditeur ne prend pas en charge l’ordre de lecture de droite à gauche et le texte commence toujours à la marge de gauche.

    > [!TIP]
    > Vous devez placer des littéraux de chaîne dans les fichiers de ressources au lieu de les coder en dur dans vos programmes. Pour plus d’informations, consultez [Ressources dans les applications de bureau (.NET Framework)](/dotnet/framework/resources/index).

    > [!NOTE]
    > Vous devez être cohérent dans votre façon de faire référence aux objets nommés en arabe et en hébreu. Par exemple, si vous utilisez des signes kachidé pour nommer une variable en arabe, vous devez toujours utiliser des signes kachidé dans vos références à cette variable, sinon une erreur se produit.

- Commentaires de code. Vous pouvez créer des commentaires en arabe ou en hébreu. Vous pouvez également utiliser ces langues dans le générateur de commentaires.