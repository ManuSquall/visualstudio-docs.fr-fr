---
title: "Options, &#201;diteur de texte, Tous les langages, Onglets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs"
helpviewer_keywords: 
  - "retraits, Éditeur de Code"
  - "Éditeur de code, comportement par défaut"
  - "onglets, configuration dans l’Éditeur de code"
  - "Tous les langages, boîte de dialogue Options de l'Éditeur de texte"
  - "éditeurs, Éditeur de code"
  - "Éditeur de code, mise en retrait"
  - "Éditeur de code, onglets"
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Options, &#201;diteur de texte, Tous les langages, Onglets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de modifier le comportement par défaut de l'éditeur de code.  Ces paramètres s'appliquent aussi aux autres éditeurs fondés sur l'éditeur de code, comme l'affichage en mode Source du Concepteur HTML.  Pour afficher ces options, sélectionnez **Options** dans le menu **Outils**.  Dans le dossier **Éditeur de texte**, développez le sous\-dossier **Tous les langages**, puis choisissez **Tabulations**.  
  
> [!CAUTION]
>  Cette page définit les options par défaut de tous les langages de développement.  Souvenez\-vous que la réinitialisation d'une option dans cette boîte de dialogue réinitialise les options Tabulations de tous les langages aux choix effectués, quels qu'ils soient.  Pour modifier les options de l'éditeur de texte d'un seul langage, développez le sous\-dossier de ce langage et sélectionnez ses pages d'options.  
  
 Si des paramètres différents sont sélectionnés dans les pages d'options Tabulations de langages de programmation particuliers, le message "Les paramètres de mise en retrait pour les formats de texte individuels sont en conflit" s'affiche pour les options **Mise en retrait** qui diffèrent et le message "Les paramètres de tabulation pour les formats de texte individuels sont en conflit" s'affiche pour les options **Tabulation** qui diffèrent.  Par exemple, ce rappel s'affiche si l'option **Mise en retrait intelligente** est sélectionnée pour Visual Basic, mais que l'option **Mise en retrait de bloc** est sélectionnée pour Visual C\+\+.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Mise en retrait  
 Aucun  
 Lorsque cette option est sélectionnée, les nouvelles lignes ne sont pas mises en retrait.  Le point d'insertion est placé dans la première colonne d'une nouvelle ligne.  
  
 Bloc  
 Lorsque cette option est sélectionnée, les nouvelles lignes sont automatiquement mises en retrait.  Le point d'insertion est placé sur le même point de départ que la ligne précédente.  
  
 Intelligente  
 Lorsque cette option est sélectionnée, les nouvelles lignes sont positionnées de manière à s'adapter au contexte du code, conformément à d'autres paramètres de mise en forme de code et aux conventions IntelliSense de votre langage de développement.  Cette option n'est pas disponible pour tous les langages de développement.  
  
 Par exemple, les lignes comprises entre une accolade ouvrante \({\) et une accolade fermante \(}\) peuvent être automatiquement mises en retrait d'un taquet de tabulation supplémentaire à partir de la position des accolades alignées.  
  
## Tabulations  
 Taille des tabulations  
 Définit la distance en espaces entre les taquets de tabulation.  La valeur par défaut est quatre espaces.  
  
 Taille du retrait  
 Définit la taille, en espaces, d'une mise en retrait automatique.  La valeur par défaut est quatre espaces.  Des tabulations et\/ou des espaces seront insérés pour occuper la taille spécifiée.  
  
 Insérer des espaces  
 Lorsque cette option est sélectionnée, les opérations de mise en retrait insèrent uniquement des espaces et non des tabulations.  Si par exemple **Taille du retrait** a la valeur 5, cinq espaces sont insérés lorsque vous appuyez sur la touche TAB ou le bouton **Augmenter le retrait** de la barre d'outils **Mise en forme**.  
  
 Conserver les tabulations  
 Lorsque cette option est sélectionnée, les opérations de mise en retrait insèrent autant de tabulations que possible.  Chaque tabulation remplit le nombre d'espaces spécifié dans **Taille des tabulations**.  Si la valeur de **Taille du retrait** n'est pas un multiple pair de la valeur de **Taille des tabulations**, des espaces sont ajoutés pour remplir la différence.  
  
## Voir aussi  
 [Options, Éditeur de texte, Tous les langages](../../ide/reference/options-text-editor-all-languages.md)   
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)