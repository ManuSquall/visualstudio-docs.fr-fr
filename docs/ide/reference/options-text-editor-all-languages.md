---
title: "Options, &#201;diteur de texte, Tous les langages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.General"
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.General"
  - "vs.toolsoptionspages.text_editor.all_languages.scrollbars"
helpviewer_keywords: 
  - "éditeur de texte (boîte de dialogue Options)"
  - "saisie semi-automatique des instructions"
  - "retour automatique à la ligne"
  - "Général (boîte de dialogue)"
  - "numéros de ligne"
  - "espace virtuel"
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Options, &#201;diteur de texte, Tous les langages
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de modifier le comportement par défaut de l'éditeur de code.  Ces paramètres s'appliquent aussi aux autres éditeurs fondés sur l'éditeur de code, comme l'affichage en mode Source du Concepteur HTML.  Pour ouvrir la boîte de dialogue, sélectionnez **Options** dans le menu **Outils**.  Dans le dossier **Éditeur de texte**, développez le sous\-dossier **Tous les langages**, puis choisissez **Général**.  
  
> [!CAUTION]
>  Cette page définit les options par défaut de tous les langages de développement.  Souvenez\-vous que la réinitialisation d'une option dans cette boîte de dialogue réinitialise les options Général de tous les langages aux choix effectués, quels qu'ils soient.  Pour modifier les options de l'éditeur de texte d'un seul langage, développez le sous\-dossier de ce langage et sélectionnez ses pages d'options.  
  
 Une coche grisée s'affiche quand une option a été sélectionnée sur les pages d'options Général de certains langages de programmation, à l'exclusion d'autres.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Compléter automatiquement les instructions  
 Répertorier automatiquement les membres  
 En cas de sélection, les listes contextuelles des membres disponibles, les propriétés, les valeurs ou les méthodes sont affichées par IntelliSense tandis que vous tapez dans l'éditeur.  Sélectionnez un élément dans la liste contextuelle pour l'insérer dans votre code.  La sélection de cette option active l'option **Masquer les membres avancés**.  
  
 Masquer les membres avancés  
 Lorsque cette option est sélectionnée, les listes de saisie automatique d'instructions se limitent à l'affichage des éléments les plus couramment utilisés.  Les autres éléments sont filtrés dans la liste.  
  
 Information sur les paramètres  
 En cas de sélection, la syntaxe complète de la déclaration ou procédure en cours s'affiche sous le point d'insertion dans l'éditeur, avec tous ses paramètres disponibles.  Le paramètre suivant que vous pouvez assigner est affiché en gras.  
  
## Paramètres  
 Activer l'espace virtuel  
 Lorsque cette case à cocher est sélectionnée et que l'option **Retour automatique à la ligne** est désactivée, vous pouvez cliquer au\-delà d'une ligne de l'éditeur de code et entrer un texte.  Cette fonctionnalité peut être utilisée pour placer des commentaires à un point précis en regard de votre code.  
  
 Retour automatique à la ligne  
 Lorsque cette case à cocher est activée, les parties d'une ligne qui s'étend horizontalement au\-delà de la zone de l'éditeur affichable sont automatiquement affichées sur la ligne suivante.  La sélection de cette option active l'option **Afficher des glyphes visuels pour le retour automatique à la ligne**.  
  
> [!NOTE]
>  La fonctionnalité **Espace virtuel** est désactivée quand l'option **Retour automatique à la ligne** est activée.  
  
 Afficher des glyphes visuels pour le retour automatique à la ligne  
 Lorsque cette option est sélectionnée, un indicateur de flèche de retour s'affiche à l'endroit où la ligne se poursuit à la ligne suivante.  
  
 Désactivez cette option si vous préférez ne pas afficher ces indicateurs.  
  
> [!NOTE]
>  Ces flèches de rappel ne sont pas ajoutées à votre code et ne sont pas imprimées.  Elles ne sont utilisées qu'à titre de référence.  
  
 Appliquer les commandes Couper ou Copier aux lignes vides en l'absence de sélection  
 Cette option définit le comportement de l'éditeur lorsque vous placez le point d'insertion sur une ligne vide, sélectionnez l'option Aucun, puis les options Copier ou Couper.  
  
-   Lorsque cette option est sélectionnée, la ligne vide est copiée ou coupée.  Si vous cliquez ensuite sur Coller, une nouvelle ligne vide est insérée.  
  
-   Lorsque cette option est désactivée, la commande Couper supprime les lignes vides.  Toutefois, les données du Presse\-papiers sont conservées.  Ainsi, si vous utilisez ensuite la commande Coller, le dernier contenu copié dans le presse\-papiers est collé.  Si vous n'avez rien copié auparavant, rien n'est collé.  
  
 Ce paramètre n'a aucun effet sur les commandes Copier ou Couper lorsqu'une ligne n'est pas vide.  Si rien n'est sélectionné, toute la ligne est copiée ou coupée.  Si vous cliquez ensuite sur Coller, le texte de la ligne tout entière et son caractère de ligne de fin sont collés.  
  
> [!TIP]
>  Pour afficher les indicateurs d'espaces, de tabulations et de fins de ligne et distinguer les lignes en retrait de celles qui sont complètement vides, sélectionnez **Avancé** dans le menu **Edition**, puis sélectionnez **Afficher les blancs**.  
  
## Affichage  
 Numéros de ligne  
 Lorsque cette case à cocher est activée, un numéro s'affiche à côté de chaque ligne de code.  
  
> [!NOTE]
>  Ces numéros de ligne ne sont pas ajoutés à votre code et ne sont pas imprimés.  Elles ne sont utilisées qu'à titre de référence.  
  
 Activer la navigation dans les URL par simple clic  
 Si cette option est sélectionnée, le curseur prend la forme d'une main avec un doigt pointé lorsqu'il passe sur une URL dans l'éditeur.  Vous pouvez cliquer sur l'URL pour afficher la page indiquée dans votre navigateur Web.  
  
 Barre de navigation  
 Lorsque cette case à cocher est activée, la **Barre de navigation** s'affiche en haut de l'éditeur de code.  Ses listes déroulantes **Objets** et **Membres** vous permettent de choisir un objet particulier dans votre code, d'effectuer une sélection à partir de ses membres et de naviguer jusqu'à la déclaration du membre sélectionné dans l'éditeur de code.  
  
## Voir aussi  
 [Options, Éditeur de texte, Tous les langages, Onglets](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)   
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)