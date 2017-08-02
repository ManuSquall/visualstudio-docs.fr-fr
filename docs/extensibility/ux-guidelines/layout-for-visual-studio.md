---
title: "Pr&#233;sentation de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Pr&#233;sentation de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La majorité des boîtes de dialogue Visual Studio sont [Mise en page de la boîte de dialogue utilitaire](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), qui sont l'unthemed boîtes de dialogue standard suivi [principes de mise en page de boîte de dialogue Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Que Visual Studio passe à actualiser son interface utilisateur, certaines des boîtes de dialogue plus apparents ont une nouvelle conception qui établit les expériences comme définition de produit. Ces [Disposition de boîte de dialogue à thème](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ont une apparence à thème.  
  
##  <a name="BKMK_UtilityDialogLayout"></a> Mise en page de la boîte de dialogue utilitaire  
  
-   Tous les contrôles dans une boîte de dialogue Utilitaire doivent démarrer à partir de l'angle supérieur gauche et flux vers le bas.  
  
-   Centre jamais des contrôles sur une boîte de dialogue pour remplir une zone importante.  
  
-   Utiliser la police d'environnement pour tout texte de la boîte de dialogue. Lorsque vous écrivez une spécification visual, spécifier la police d'environnement au lieu de sélectionner une police particulière et une taille. Consultez [La police d'environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Utiliser l'espacement du contrôle de cohérence et positionnement pour prendre en charge l'objectif de la qualité de savoir\-faire.  
  
-   Boîtes de dialogue peuvent devenir plus complexes à partir d'un plus grand nombre de contrôles, une unique juxtaposition des contrôles ou des deux. Dans ce cas complex, permettre suffisamment d'espace entre les groupes de contrôle à l'utilisateur un flux logique d'analyse.  
  
### Exemples de mise en page de boîte de dialogue utilitaire  
 Toutes les dimensions sont exprimées en pixels.  
  
 ![Dialog spacing for labels above controls](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801\-a\_UtilitySpacingAbove")  
  
 **Figure 08.01\-a: Espacement des lignes directrices pour les boîtes de dialogue utilitaire avec étiquettes au\-dessus des contrôles**  
  
 ![Dialog spacing for labels to the left of controls](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801\-b\_UtilitySpacingLeft")  
  
 **Figure 08.01\-b: Espacement des lignes directrices pour les boîtes de dialogue utilitaire avec des étiquettes à gauche des contrôles**  
  
### Détails de la mise en page  
  
#### Marges  
  
-   Toutes les boîtes de dialogue doivent avoir une bordure de 12 pixels autour de tous les bords.  
  
-   Marges dans un cadre de groupe doivent être 9 pixels entre le bord du cadre.  
  
-   Les marges d'un contrôle onglet doivent être 6 pixels du bord du contrôle onglet.  
  
#### Boutons de commande  
  
-   Boutons de commande fonctionnent dans le cadre de la boîte de dialogue, pas sur le contenu. Ils doivent être placés dans la partie inférieure droite et doivent avoir suffisamment d'espace variable ci\-dessus pour définir les boutons distinctes.  
  
-   S'il existe des boutons horizontales qui opèrent dans la boîte de dialogue, la configuration du bouton autre commande est une pile verticale en haut à droite. Consultez [Boutons de commande intérieurs](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) ci\-dessous.  
  
-   L'espace à gauche des boutons de commande \(gauche\/centrale inférieure de la boîte de dialogue\) est considéré comme partie de la « bande » de contrôles de boîte de dialogue opération. La seule chose qui doit empiéter sur cet espace est un lien d'aide correspondant à la tâche globale ou de la boîte de dialogue.  
  
-   Boutons de commande doit être x 23 75 pixels.  
  
-   Boutons de commande doit être éloignés de 6 pixels.  
  
 ![Basic button alignment](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801\-c\_ButtonAlign")  
  
 **Figure 08.01\-c: Alignement des boutons de base**  
  
#### Étiquettes  
  
-   Aligner à gauche toutes les étiquettes.  
  
-   Pour les étiquettes qui se trouvent au\-dessus d'un contrôle, ils doivent aligner à gauche précisément avec le contrôle en dessous et en bas de l'étiquette doit être 5 pixels au\-dessus de l'autre contrôle \(par exemple, une zone de liste déroulante\).  
  
-   Pour les étiquettes qui se trouvent à gauche des contrôles, la largeur minimale entre l'étiquette et le contrôle d'entrée est de 10 pixels. Une deuxième colonne implicite doit être établie pour aligner les zones de texte, zones de liste déroulante ou d'autres contrôles.  
  
-   Étiquettes sont de casse de la phrase et sont suivis par un signe deux\-points. Consultez [Style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### Distance entre les contrôles  
 Contrôles de pile raisonnablement. Il n'existe aucune règle absolue pour l'espacement entre les contrôles empilées. La précision entre les contrôles peut varier légèrement entre les boîtes de dialogue. L'espacement recommandée est 20 pixels pour les paires de contrôle\/étiquette verticale et 9 pixels pour les paires contrôle horizontal\/étiquette. L'espacement minimal de contrôles pour les paires horizontales est 6 pixels.  
  
 ![Recommended distance between controls](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801\-d\_ControlDistance")  
  
 **Figure 08.01\-d: Des recommandations pour la distance entre les contrôles**  
  
#### Mise en retrait du contrôle  
 Lorsque les contrôles sont imbriqués, aligner des contrôles internes horizontalement avec le bord gauche du contrôle ci\-dessus, généralement l'étiquette.  
  
 ![Nested control alignment](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801\-e\_ControlAlign")  
  
 **Figure 08.01\-e: Alignement des contrôles imbriqués**  
  
#### Largeur du contrôle  
 La largeur d'une zone de texte ou d'autres contrôles similaires doit être inférieure à la moyenne d'entrée pour le champ. La moyenne des mots anglais sont de cinq caractères. Par exemple, une zone de texte qui nécessite un nom long chemin d'accès doit être dans la mesure où la disposition horizontale permet, tandis que d'une liste déroulante pour les noms de plateforme doivent être uniquement une longueur permettant l'entrée la plus longue.  
  
#### Texte d'aide  
  
-   Une boîte de dialogue peut afficher le texte d'aide qui fournit des informations supplémentaires sur l'objectif de la boîte de dialogue. En général, cela se trouve en haut et peut être des phrases de 1 à 2.  
  
-   La longueur de ligne doit être une largeur à l'aise pour un utilisateur à analyser et à lire. Une boîte de dialogue moyenne doit être pas plus de 550 pixels de large.  
  
####  <a name="BKMK_InteriorCommandButtons"></a> Boutons de commande intérieurs  
 Dans les boîtes de dialogue plus complexes, un contrôle interne peut avoir ses propres boutons connexes, ce qui peut affecter l'emplacement où se trouvent les boutons de validation de la boîte de dialogue.  
  
-   Utilisez un alignement vertical \(colonne\) de l'intérieur des boutons lorsque **OK**\/**Annuler** est orienté horizontalement dans le coin inférieur droit.  
  
-   Utilisez un alignement horizontal \(ligne\) de l'intérieur des boutons lorsque **OK**\/**Annuler** est orienté verticalement dans le coin supérieur droit. Cette situation est moins courante.  
  
-   Taille du bouton intérieurs doit cibler la taille des boutons standard de pixels correspondant à la taille de 75 x 23 **OK**\/**Annuler** boutons lorsque cela est possible. Si une étiquette de bouton rend le bouton de dépassement de la taille du bouton standard, les autres boutons de ce groupe doivent s'aligner avec cette taille plus importante.  
  
 ![Horizontal OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801\-f\_HorizOKCan")  
  
 **Figure 08.01\-f: Boutons intérieur Vertical horizontal OK\/Annuler**  
  
 ![Vertical OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801\-g\_VertOKCan")  
  
 **Figure 08.01\-g: Horizontal intérieur boutons OK\/Annuler verticaux**  
  
#### \[Parcourir...\] bouton  
 **\[Parcourir...\]** boutons qui suivent une zone de texte doit spécifier « Parcourir... » dans sa totalité, y compris les points de suspension. Si l'espace est limité ou s'il existe plusieurs **\[Parcourir...\]** boutons à l'écran, le bouton peut être réduit à simplement les points de suspension.  
  
##  <a name="BKMK_ThemedDialogLayout"></a> Disposition de boîte de dialogue à thème  
 Boîtes de dialogue à thème dans Visual Studio ont une apparence plus claire et offrent davantage d'espace blanc. Typographie fournit plus l'accent et présentant un intérêt, offre l'interligne plus ouvert et une variation de poids et de tailles de police. Si possible, barres de chrome et le titre ont été réduits ou supprimés. La disposition de ces boîtes de dialogue doit suivre ce modèle de base :  
  
1.  L'arrière\-plan de la boîte de dialogue est blanc.  
  
2.  Il existe une bordure de 1 pixel règle dans un gris de la valeur moyenne.  
  
3.  Le titre de la boîte de dialogue ne plus se trouve dans une barre de titre, mais fournit un intérêt visuel et accentuation dans une taille supérieure. \(Voir la section de taille de police de [Style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).\)  
  
4.  Les étiquettes couplés avec un texte supplémentaire, par exemple une description, doivent être **police d'environnement \+ gras**.  
  
5.  Colonnes intérieurs sont séparés par une règle de 1 pixel en gris clair.  
  
6.  Par défaut ne disposer d'aucun trait de soulignement. États survol et enfoncés ont un changement de couleur suivi d'un trait de soulignement.  
  
7.  Valider des boutons \(comme **OK**\/**Annuler**\) se trouvent dans le coin inférieur droit.  
  
### Exemples de mise en page de boîte de dialogue à thème  
 ![Themed dialog layout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801\-h\_ThemedDialog")  
  
 **Figure 08.01\-h: Boîte de dialogue à thème**  
  
 ![Themed dialog dimensions](~/docs/extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801\-i\_ThemedDialogDimensions")  
  
 **Figure 08.01\-i Dialogue à thème – Dimensions**  
  
 ![Themed dialog fonts](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801\-j\_ThemedDialogFonts")  
  
 **Figure 08.01\-j: Dialogue à thème : polices**  
  
 ![Themed dialog colors](~/docs/extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801\-k\_ThemedDialogColors")  
  
 **Figure 08.01\-k: Dialogue à thème – couleurs**  
  
## Voir aussi  
 [Modèles d'application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Contrôles \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Boîtes de dialogue \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)