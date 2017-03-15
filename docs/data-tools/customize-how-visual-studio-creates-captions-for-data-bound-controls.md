---
title: "Comment&#160;: personnaliser la fa&#231;on dont Visual Studio cr&#233;e des l&#233;gendes pour les contr&#244;les li&#233;s aux donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "légendes, lié aux données"
  - "Sources de données (fenêtre), légendes des étiquettes"
  - "légendes des étiquettes, Sources de données (fenêtre)"
  - "légendes intelligentes"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: personnaliser la fa&#231;on dont Visual Studio cr&#233;e des l&#233;gendes pour les contr&#244;les li&#233;s aux donn&#233;es
Une considération particulière entre en jeu lorsque vous faites glisser des éléments de la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md) sur le Concepteur Windows Forms : le nom des colonnes dans les étiquettes des légendes est reformaté en chaîne plus lisible lorsque plusieurs mots sont concaténés.  Vous pouvez personnaliser la façon dont ces étiquettes sont créées en définissant les valeurs **SmartCaptionExpression**, **SmartCaptionReplacement** et **SmartCaptionSuffix** dans la clé de Registre **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\10.0\\Concepteurs de données**.  
  
> [!NOTE]
>  Cette clé de Registre n'existe pas tant que vous ne la créez pas.  
  
 La retouche des légendes \(smart captioning\) est contrôlée par l'expression régulière entrée dans la valeur **SmartCaptionExpression**.  L'ajout de la clé de Registre **Concepteurs de données** substitue l'expression régulière par défaut qui contrôle les légendes.  Pour plus d'informations sur les expressions régulières, consultez .[Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Le tableau suivant décrit les valeurs de Registre qui contrôlent les étiquettes des légendes.  
  
|Élément du Registre|Description|  
|-------------------------|-----------------|  
|SmartCaptionExpression|Expression régulière utilisée pour correspondre à vos modèles.|  
|SmartCaptionReplacement|Format d'affichage des groupes appariés dans **SmartCaptionExpression**.|  
|SmartCaptionSuffix|Chaîne facultative à ajouter à la fin de la légende.|  
  
 Le tableau suivant répertorie les paramètres internes par défaut pour ces valeurs de Registre.  
  
|Élément|Valeur par défaut|Explication|  
|-------------|-----------------------|-----------------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\)\(\\\\p{Lu}\)&#124;\_\+|Correspond à un caractère minuscule suivi d'un caractère majuscule ou d'un trait de soulignement.|  
|**SmartCaptionReplacement**|$1 $2|$1 représente les caractères appariés dans la première parenthèse de l'expression et $2 les caractères appariés dans la deuxième parenthèse.  Ils sont remplacés par la première correspondance, un espace, puis la deuxième correspondance.|  
|**SmartCaptionSuffix**|:|Représente un caractère ajouté à la chaîne retournée.  Par exemple, si la légende est `Company Name`, le suffixe la transforme en `Company Name:`.|  
  
> [!CAUTION]
>  Vous devez être très prudent lorsque vous entreprenez une quelconque action dans l'Éditeur du Registre.  Sauvegardez le Registre avant de le modifier.  L'utilisation incorrecte de l'Éditeur du Registre peut provoquer de sérieux problèmes qui peuvent nécessiter la réinstallation du système d'exploitation.  Microsoft ne garantit pas que les problèmes que vous provoquez à la suite d'une utilisation incorrecte de l'Éditeur du Registre peuvent être résolus.  Utilisez\-le à vos risques et périls.  
>   
>  L'article suivant de la base de connaissances contient des instructions sur la sauvegarde, la modification et la restauration du Registre : [Description du Registre de Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) \(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\)  
  
### Pour modifier le comportement de retouche des légendes dans la fenêtre Sources de données  
  
1.  Ouvrez une fenêtre Commande en cliquant sur **Démarrer**, puis sur **Exécuter**.  
  
2.  Tapez `regedit` dans la boîte de dialogue **Exécuter**, puis cliquez sur **OK**.  
  
3.  Développez le nœud **HKEY\_CURRENT\_USER**.  
  
4.  Développez le nœud **Logiciel**.  
  
5.  Développez le nœud **Microsoft**.  
  
6.  Développez le nœud **VisualStudio**.  
  
7.  Cliquez avec le bouton droit sur le nœud **10.0** et créez une **Clé** nommée `Concepteurs de données`.  
  
8.  Cliquez avec le bouton droit sur le nœud **Concepteurs de données** et créez une **Valeur de chaîne** nommée `SmartCaptionExpression`.  
  
9. Cliquez avec le bouton droit sur le nœud **Concepteurs de données** et créez une **Valeur de chaîne** nommée `SmartCaptionReplacement`.  
  
10. Cliquez avec le bouton droit sur le nœud **Concepteurs de données** et créez une **Valeur de chaîne** nommée `SmartCaptionSuffix`.  
  
11. Cliquez avec le bouton droit sur l'élément **SmartCaptionExpression** puis sélectionnez **Modifier**.  
  
12. Entrez l'expression régulière que vous voulez que la fenêtre **Sources de données** utilise.  
  
13. Cliquez avec le bouton droit sur l'élément **SmartCaptionReplacement** puis sélectionnez **Modifier**.  
  
14. Entrez la chaîne de remplacement mise en forme de la façon dont vous voulez afficher les modèles appariés dans votre expression régulière.  
  
15. Cliquez avec le bouton droit sur l'élément **SmartCaptionSuffix** puis sélectionnez **Modifier**.  
  
16. Entrez les caractères que vous voulez afficher à la fin de la légende.  
  
     La prochaine fois que vous ferez glisser des éléments de la fenêtre **Sources de données**, les légendes seront créées à l'aide des nouvelles valeurs de Registre fournies.  
  
### Pour désactiver la fonctionnalité de retouche des légendes \(smart captioning\)  
  
1.  Ouvrez une fenêtre Commande en cliquant sur **Démarrer**, puis sur **Exécuter**.  
  
2.  Tapez `regedit` dans la boîte de dialogue **Exécuter**, puis cliquez sur **OK**.  
  
3.  Développez le nœud **HKEY\_CURRENT\_USER**.  
  
4.  Développez le nœud **Logiciel**.  
  
5.  Développez le nœud **Microsoft**.  
  
6.  Développez le nœud **VisualStudio**.  
  
7.  Cliquez avec le bouton droit sur le nœud **10.0** et créez une **Clé** nommée `Concepteurs de données`.  
  
8.  Cliquez avec le bouton droit sur le nœud **Concepteurs de données** et créez une **Valeur de chaîne** nommée `SmartCaptionExpression`.  
  
9. Cliquez avec le bouton droit sur le nœud **Concepteurs de données** et créez une **Valeur de chaîne** nommée `SmartCaptionReplacement`.  
  
10. Cliquez avec le bouton droit sur le nœud **Concepteurs de données** et créez une **Valeur de chaîne** nommée `SmartCaptionSuffix`.  
  
11. Cliquez avec le bouton droit sur l'élément **SmartCaptionExpression** puis sélectionnez **Modifier**.  
  
12. Entrez `(. *)` pour la valeur.  Cela fera correspondre la chaîne entière.  
  
13. Cliquez avec le bouton droit sur l'élément **SmartCaptionReplacement** puis sélectionnez **Modifier**.  
  
14. Entrez `$1` pour la valeur.  Cela remplace la chaîne par la valeur appariée, qui est la chaîne entière, afin qu'elle reste inchangée.  
  
     La prochaine fois que vous ferez glisser des éléments de la fenêtre **Sources de données**, les légendes seront créées avec des légendes non modifiées.  
  
## Voir aussi  
 [Expressions régulières du .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)