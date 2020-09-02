---
title: Polices et couleurs, Environnement, boîte de dialogue Options
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d5c9edd47e3db43735d3c6e8f6a4ec1a881214e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595616"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Polices et couleurs, Environnement, boîte de dialogue Options

La page **Polices et couleurs** de la boîte de dialogue **Options** vous permet d’établir un jeu de polices et un modèle de couleurs personnalisés pour divers éléments d’interface utilisateur dans l’environnement de développement intégré (IDE). Vous pouvez accéder à cette boîte de dialogue en cliquant sur **Outils**  >  **options**, **Environment**puis en sélectionnant  >  **polices et couleurs de**l’environnement.

Les modifications apportées à un modèle de couleurs ne sont pas prises en compte lors de la session au cours de laquelle vous avez effectué ces changements. Vous pouvez évaluer les changements de couleurs en ouvrant une autre instance de Visual Studio, et en reproduisant les conditions dans lesquelles vous souhaitez qu'ils soient appliqués.

**Afficher les paramètres de**

Répertorie tous les éléments d'interface utilisateur pour lesquels vous pouvez modifier le jeu de polices et le modèle de couleurs. Après avoir sélectionné un élément dans cette liste, vous pouvez personnaliser les paramètres de couleurs de l’élément sélectionné dans **Éléments affichés**.

- **Éditeur de texte**

     Les modifications apportées aux paramètres d'affichage du style, de la taille et de la couleur des polices dans l'éditeur de texte influencent la présentation du texte dans l'éditeur de texte par défaut. Les documents ouverts dans un éditeur de texte en dehors de l'IDE ne sont pas affectés par ces paramètres.

- **Imprimante**

     Les modifications apportées aux paramètres d'affichage du style, de la taille et de la couleur des polices de l'imprimante influencent la présentation du texte sur les documents imprimés.

    > [!NOTE]
    > Selon les besoins, vous pouvez sélectionner une autre police par défaut pour l'impression que celle utilisée pour l'affichage dans l'éditeur de texte. Cela peut être utile lors de l'impression de code contenant des caractères codés sur un octet et sur deux octets.

- **Compléter automatiquement les instructions**

     Change le style de police et la taille du texte affichés par la fonctionnalité de saisie semi-automatique des instructions dans l'éditeur.

- **Info-bulle de l’éditeur**

     Change le style de police et la taille du texte des info-bulles affichées dans l'éditeur.

- **Police d’environnement**

     Modifie le style de police et la taille de tous les éléments de l’interface utilisateur IDE qui n’ont pas déjà une option distincte dans **afficher les paramètres de**.

     ::: moniker range="vs-2017"

     Par exemple, cette option s’applique à la **Page de démarrage** mais n’affecte pas la fenêtre **Sortie**.

     ::: moniker-end

- **[Toutes les fenêtres Outil de texte]**

     Les changements apportés aux paramètres de style, de taille et d'affichage des couleurs de la police pour cet élément affectent l'apparence du texte dans les fenêtres Outil qui ont des volets de sortie dans l'IDE. C'est le cas, par exemple, de la fenêtre Sortie, la fenêtre Commande, la fenêtre Exécution, etc.

    > [!NOTE]
    > Les modifications apportées au texte des éléments **[toutes les fenêtres outil de texte]** ne prennent pas effet au cours de la session dans laquelle vous les apportez. Vous pouvez évaluer ces changements en ouvrant une autre instance de Visual Studio.

**Par défaut**

Réinitialise les valeurs de couleur et de police de l’élément de liste sélectionné dans **Afficher les paramètres de**. Le bouton **Utiliser** s’affiche quand d’autres modèles d’affichage sont disponibles pour la sélection. Par exemple, vous avez le choix entre deux modèles pour l'imprimante.

**Police (les polices à largeur fixe sont en gras)**

Répertorie toutes les polices installées sur votre ordinateur. Quand le menu déroulant s’affiche pour la première fois, la police active de l’élément sélectionné dans le champ **Afficher les paramètres de** est mise en surbrillance. Les polices fixes, qui sont plus faciles à aligner dans l'éditeur, s'affichent en gras.

**Taille**

Répertorie les tailles en points disponibles pour la police sélectionnée. Le changement de taille de la police affecte tous les **éléments affichés** de la sélection dans **Afficher les paramètres de**.

**Éléments affichés**

Répertorie les éléments dont vous pouvez modifier la couleur de premier plan et d'arrière-plan.

> [!NOTE]
> **Texte brut** est l’élément d’affichage par défaut. Ainsi, les propriétés assignées à **Texte brut** sont remplacées par les propriétés assignées aux autres éléments d’affichage. Par exemple, si vous assignez la couleur bleue à **Texte brut** et la couleur verte à **Identificateur**, tous les identificateurs s’affichent en vert. Dans cet exemple, les propriétés associées à **Identificateur** remplacent les propriétés associées à **Texte brut**.

Voici certains éléments d'affichage :

|Élément d'affichage|Description|
|------------------|-----------------|
|**Texte brut**|Texte dans l'éditeur.|
|**Texte sélectionné**|Texte inclus dans la sélection actuelle quand l'éditeur a le focus.|
|**Texte sélectionné inactif**|Texte inclus dans la sélection actuelle quand l'éditeur a perdu le focus.|
|**Marge des indicateurs**|marge à gauche de l’éditeur de code où sont affichés les points d’arrêt et les icônes de signet.|
|**Numéros de ligne**|Numéros facultatifs qui apparaissent en regard de chaque ligne de code|
|**Espaces blancs visibles**|Indicateurs des espaces, des onglets et du retour automatique à la ligne|
|**Signet**|Lignes qui ont des signets. Le **signet** n’est visible que si la marge des indicateurs est désactivée.|
|**Accolades correspondantes (en surbrillance)**|Mise en surbrillance généralement en gras pour la correspondance des accolades.|
|**Accolades correspondantes (rectangle)**|Mise en surbrillance qui correspond généralement à un rectangle gris à l'arrière-plan.|
|**Point d’arrêt (Désactivé)**|Non utilisé.|
|**Point d’arrêt (activé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt simples. Cette option est applicable uniquement si les points d’arrêt au niveau de l’instruction sont actifs ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt (erreur)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt à l'état d'erreur. Applicable uniquement si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt (avertissement)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt à l'état d'avertissement. Applicable uniquement si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Avancé (Désactivé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt conditionnels ou prenant en charge le nombre d'accès, et qui sont désactivés. Applicable uniquement si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Avancé (Activé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt conditionnels ou prenant en charge le nombre d'accès. Applicable uniquement si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Avancé (Erreur)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt conditionnels ou prenant en charge le nombre d'accès, et qui sont à l'état d'erreur. Applicable uniquement si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Avancé (Avertissement)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt conditionnels ou prenant en charge le nombre d'accès, et qui sont à l'état d'avertissement. Applicable uniquement si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Mappé (Désactivé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt mappés désactivés. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Mappé (Activé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt mappés. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Mappé (Erreur)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt mappés à l'état d'erreur. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point d’arrêt - Mappé (Avertissement)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points d'arrêt mappés à l'état d'avertissement. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Mots clés d’utilisateur C/C++**|Constante dans un fichier de code particulier défini par la directive `#define`.|
|**Retour d’appel**|Spécifie la couleur de mise en surbrillance des instructions ou lignes sources qui indiquent les points de retour d'appel quand le contexte passe à un frame de pile non supérieur durant le débogage.|
|**Champ dépendant d’extrait de code**|Champ mis à jour quand le champ modifiable actuel est modifié.|
|**Champ d’extrait de code**|Champ modifiable quand un extrait de code est actif.|
|**Texte réductible**|Bloc de texte ou de code qui peut être affiché et masqué dans l'éditeur de code.|
|**Commentaire**|Commentaires de code.|
|**Erreur du compilateur**|Soulignements ondulés (ou tildes) bleus dans l'éditeur indiquant une erreur de compilation.|
|**Zone non couverte**|Code non couvert par un test unitaire.|
|**Zone partiellement couverte**|Code partiellement couvert par un test unitaire.|
|**Zone couverte**|Code complètement couvert par un test unitaire.|
|**Commentaire CSS**|Commentaire dans des feuilles de style en cascade. Par exemple :<br /><br /> /* commentaire \*/|
|**Mot clé CSS**|Mots clés dans la feuille de style en cascade.|
|**Nom de propriété CSS**|Nom d'une propriété, par exemple Background.|
|**Valeur de propriété CSS**|Valeur assignée à une propriété, par exemple blue.|
|**Sélecteur CSS**|Chaîne qui identifie les éléments auxquels s'applique la règle correspondante. Un sélecteur peut être un sélecteur simple, tel que 'H1', ou un sélecteur contextuel, tel que 'H1 B', qui se compose de plusieurs sélecteurs simples.|
|**Valeur de chaîne CSS**|Chaîne dans des feuilles de style en cascade.|
|**Emplacement de la liste en cours**|Ligne actuelle dans une fenêtre d'outil liste, telle que la fenêtre Sortie ou la fenêtre Résultats de la recherche.|
|**Instruction en cours**|Spécifie la couleur de mise en surbrillance de l'instruction ou de la ligne source qui indique la position actuelle de l'exécution pas à pas durant le débogage.|
|**Données du débogueur modifiées**|Couleur de texte utilisée pour afficher les données modifiées dans les fenêtres **Registres** et **Mémoire**.|
|**Arrière-plan de la fenêtre Définition**|Couleur d’arrière-plan de la fenêtre **Définition de code**.|
|**Correspondance active de la fenêtre Définition**|Définition actuelle dans la fenêtre **Définition de code**.|
|**Nom de fichier du code machine**|Couleur de texte utilisée pour afficher les décompositions de nom de fichier dans la fenêtre **Code Machine**.|
|**Source du code machine**|Couleur de texte utilisée pour afficher les lignes sources dans la fenêtre **Code Machine**.|
|**Symbole du code machine**|Couleur de texte utilisée pour afficher les noms de symboles dans la fenêtre **Code Machine**.|
|**Texte du code machine**|Couleur de texte utilisée pour afficher le code d’opération et les données dans la fenêtre **Code Machine**.|
|**Code exclu**|Code qui ne doit pas être compilé, en raison d'une directive de préprocesseur conditionnelle telle que `#if`.|
|**Identificateur**|Identificateurs présents dans le code, par exemple les noms des classes, des méthodes et des variables.|
|**Mot clé**|Mots clés réservés du langage donné. Exemple : class et namespace.|
|**Adresse mémoire**|Couleur de texte utilisée pour afficher la colonne d’adresse dans la fenêtre **Mémoire**.|
|**Mémoire modifiée**|Couleur de texte utilisée pour afficher les données modifiées dans la fenêtre **Mémoire**.|
|**Données de la mémoire**|Couleur de texte utilisée pour afficher les données à l’intérieur de la fenêtre **mémoire** .|
|**Mémoire illisible**|Couleur de texte utilisée pour afficher les zones de mémoire illisibles dans la fenêtre **Mémoire**.|
|**Nombre**|Nombre dans du code, qui représente une valeur numérique réelle.|
|**Opérateur**|Opérateurs tels que +, - et !=.|
|**Autre erreur**|Autres types d'erreurs non couverts par d'autres tildes d'erreur. Actuellement, cela inclut les modifications non applicables dans Modifier & Continuer.|
|**Mot clé de préprocesseur**|Mots clés utilisés par le préprocesseur tels que #include.|
|**Zone en lecture seule**|Code qui ne peut pas être modifié. Il s'agit, par exemple, du code affiché dans la fenêtre Définition de code, ou du code qui ne peut pas être modifié durant Modifier & Continuer.|
|**Refactorisation de l’arrière-plan**|Couleur d’arrière-plan de la boîte de dialogue **Aperçu des modifications**.|
|**Refactorisation du champ actuel**|Couleur d’arrière-plan de l’élément actuel à refactoriser dans la boîte de dialogue **Aperçu des modifications**.|
|**Refactorisation du champ dépendant**|Couleur des références de l’élément à refactoriser dans la boîte de dialogue **Aperçu des modifications**.|
|**Données du registre**|Couleur de texte utilisée pour afficher les données dans la fenêtre **Registres**.|
|**Inscrire NAT**|Couleur de texte utilisée pour afficher les données et objets non reconnus dans la fenêtre **Registres**.|
|**Balise active**|Sert à désigner le plan quand des étiquettes actives sont appelées.|
|**Marqueur SQL DML**|S'applique à l'éditeur Transact-SQL. Les instructions DML dans cet éditeur sont marquées avec un cadre englobant bleu par défaut.|
|**Code périmé**|Code annulé et remplacé en attente d'une mise à jour. Dans certains cas, Modifier & Continuer ne peut pas appliquer immédiatement les modifications du code, mais ce sera le cas plus tard, durant le débogage. Cela se produit si vous modifiez une fonction qui doit appeler la fonction en cours d'exécution, ou si vous ajoutez plus de 64 octets de nouvelles variables à une fonction en attente dans la pile des appels. Dans ce cas, le débogueur affiche la boîte de dialogue "Avertissement : code périmé". Par ailleurs, le code annulé et remplacé continue à s'exécuter jusqu'à ce que la fonction en question s'arrête et soit appelée à nouveau. Modifier & Continuer applique les modifications du code à ce moment-là.|
|**Chaîne**|Littéraux de chaîne.|
|**String (C# @ Verbatim)**|Les littéraux de chaîne en C# sont interprétés textuellement. Par exemple :<br /><br /> @"x"|
|**Erreur de syntaxe**|Erreurs d'analyse.|
|**Raccourci de la liste des tâches**|Si le raccourci **Liste des tâches** est ajouté à une ligne, et si la marge des indicateurs est désactivée, la ligne est mise en surbrillance.|
|**Point de trace (Désactivé)**|Non utilisé.|
|**Point de trace (Activé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace simples. Cette option est applicable uniquement si les points de trace au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace (erreur)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace à l'état d'erreur. Cette option est applicable uniquement si les points de trace au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace (Avertissement)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace à l'état d'avertissement. Cette option est applicable uniquement si les points de trace au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Avancé (Désactivé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace conditionnels ou prenant en charge le nombre d'accès, et qui sont désactivés. Cette option est applicable uniquement si les points de trace au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Avancé (Activé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace conditionnels ou prenant en charge le nombre d'accès. Cette option est applicable uniquement si les points de trace au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Avancé (Erreur)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace conditionnels ou prenant en charge le nombre d'accès, et qui sont à l'état d'erreur. Cette option est applicable uniquement si les points de trace au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Avancé (Avertissement)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace conditionnels ou prenant en charge le nombre d'accès, et qui sont à l'état d'avertissement. Cette option est applicable uniquement si les points de trace au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Mappé (Désactivé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace mappés désactivés. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Mappé (Activé)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace mappés. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Mappé (Erreur)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace mappés à l'état d'erreur. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Point de trace - Mappé (Avertissement)**|Spécifie la couleur de mise en surbrillance des instructions ou des lignes qui contiennent des points de trace mappés à l'état d'avertissement. Applicable pour le débogage ASP ou ASP.NET si les points d’arrêt au niveau de l’instruction sont actifs, ou si l’option **Surligner l’intégralité de la ligne source pour les points d’arrêt et l’instruction actuelle** est sélectionnée dans [Général, Débogage, boîte de dialogue Options](../../debugger/general-debugging-options-dialog-box.md).|
|**Suivi des modifications après l’enregistrement**|Lignes de code qui ont été modifiées depuis l'ouverture du fichier mais qui sont enregistrées sur le disque.|
|**Suivi des modifications avant l’enregistrement**|Lignes de code qui ont été modifiées depuis l'ouverture du fichier mais qui ne sont pas enregistrées sur le disque.|
|**Types utilisateur**|Types définis par les utilisateurs.|
|**Types utilisateur (délégués)**|Couleur de type pour les délégués.|
|**Types utilisateur (énumérations)**|Couleur de type pour les énumérations.|
|**Types utilisateur (interfaces)**|Couleur de type pour les interfaces.|
|**Types utilisateur (types valeur)**|Couleur de type pour les types valeur tels que les structs en C#.|
|**Marqueur en lecture seule Visual Basic**|Marqueur spécifique à Visual Basic pour désigner EnC, comme les régions d'exception, une définition de méthode et les frames d'appel non-feuille.|
|**Avertissement**|Avertissements du compilateur.|
|**Chemin d’accès des lignes d’avertissement**|Utilisé pour les lignes d'avertissement de l'analyse statique.|
|**Attribut XML**|Noms d'attributs.|
|**Guillemets d’attribut XML**|Guillemets pour les attributs XML.|
|**Valeur d’attribut XML**|Contenu des attributs XML.|
|**Section Cdata XML**|Contenu de \<![CDATA[...]]> .|
|**Commentaire XML**|Contenu de \<!-- -->.|
|**Délimiteur XML**|Délimiteurs de syntaxe XML, y compris <, < ?, < !, \<!--, --> , ? \> , \<![, ]]> et [,].|
|**Attribut de documentation XML**|Valeur d’un attribut de documentation XML, telle que \<param name="I"> l’endroit où le « I » est coloré.|
|**Commentaire sur la documentation XML**|Commentaires insérés dans les commentaires de la documentation xml.|
|**Étiquette de documentation XML**|Étiquettes dans les commentaires de document XML, comme<br /><br /> /// \<summary>.|
|**Mot clé XML**|Mots clés DTD tels que CDATA, IDREF et NDATA.|
|**Nom XML**|Noms d'éléments et nom de la cible des instructions de traitement.|
|**Instruction de traitement XML**|Contenu des instructions de traitement, à l'exclusion du nom de la cible.|
|**Texte XML**|Contenu de l'élément en texte brut.|
|**Mot clé XSLT**|Noms d'éléments XSLT.|

**Premier plan**

Répertorie les couleurs disponibles pour le premier plan de l’élément sélectionné dans **Éléments affichés**. Dans la mesure où certains éléments sont liés et doivent conserver un modèle d'affichage cohérent, le changement de la couleur de premier plan du texte modifie également les valeurs par défaut des éléments tels que Erreur du compilateur, Mot clé ou Opérateur.

**Automatique**

Les éléments peuvent hériter de la couleur de premier plan d’autres éléments d’affichage tels que **Texte brut**. À l'aide de cette option, quand vous modifiez la couleur d'un élément d'affichage hérité, la couleur des éléments d'affichage associés change aussi automatiquement. Par exemple, si vous avez sélectionné la valeur **Automatique** pour **Erreur du compilateur**, et si vous changez plus tard la couleur de **Texte brut** en rouge, **Erreur du compilateur** hérite aussi automatiquement de la couleur rouge.

**Par défaut**

Couleur qui s’affiche pour l’élément la première fois que vous ouvrez Visual Studio. Si vous cliquez sur le bouton **Par défaut**, la valeur initiale est restaurée à l’aide de cette couleur.

**Personnalisé**

Affiche la boîte de dialogue Couleur pour vous permettre de définir une couleur personnalisée pour l'élément sélectionné dans la liste Éléments affichés.

> [!NOTE]
> Il se peut que les paramètres de couleur de l'affichage de votre ordinateur limitent vos possibilités en matière de définition de couleurs personnalisées. Par exemple, si votre ordinateur est configuré pour afficher 256 couleurs, et si vous sélectionnez une couleur personnalisée dans la boîte de dialogue **Couleur**, l’IDE adopte par défaut la **couleur de base** la plus proche et affiche la couleur noire dans la zone d’aperçu **Couleur**.

**Arrière-plan de l’élément**

Propose une palette de couleurs disponibles pour l’arrière-plan de l’élément sélectionné dans **Éléments affichés**. Dans la mesure où certains éléments sont liés et doivent conserver un modèle d'affichage cohérent, le changement de la couleur d'arrière-plan du texte modifie également les valeurs par défaut des éléments tels que Erreur du compilateur, Mot clé ou Opérateur.

**Automatique**

Les éléments peuvent hériter de la couleur d’arrière-plan d’autres éléments d’affichage tels que **Texte brut**. À l'aide de cette option, quand vous modifiez la couleur d'un élément d'affichage hérité, la couleur des éléments d'affichage associés change aussi automatiquement. Par exemple, si vous avez sélectionné la valeur **Automatique** pour **Erreur du compilateur**, et si vous changez plus tard la couleur de **Texte brut** en rouge, **Erreur du compilateur** hérite aussi automatiquement de la couleur rouge.

**Par défaut**

Couleur qui s’affiche pour l’élément la première fois que vous ouvrez Visual Studio. Si vous cliquez sur le bouton **Par défaut**, la valeur initiale est restaurée à l’aide de cette couleur.

**Personnalisé**

Affiche la boîte de dialogue Couleur pour vous permettre de définir une couleur personnalisée pour l'élément sélectionné dans la liste Éléments affichés.

**Gras**

Sélectionnez cette option pour afficher le texte des **éléments affichés** en gras. Le texte en gras est plus facilement repérable dans l'éditeur.

**Exemple**

Affiche un aperçu du modèle de style, du modèle de taille et du modèle de couleurs de la police pour les éléments sélectionnés dans **Afficher les paramètres de** et **Éléments affichés**. Vous pouvez utiliser cette zone pour afficher un aperçu des résultats obtenus quand vous testez différentes options de mise en forme.

## <a name="see-also"></a>Voir aussi

- [Options, boîte de dialogue](../../ide/reference/options-dialog-box-visual-studio.md)
- [Comment : modifier les polices et les couleurs](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
