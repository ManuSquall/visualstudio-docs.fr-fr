---
title: "Kit de d&#233;veloppement logiciel de Microsoft Help Viewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# Kit de d&#233;veloppement logiciel de Microsoft Help Viewer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cet article contient les tâches suivantes pour les intégrateurs de la visionneuse d'aide Visual Studio :  
  
-   Création d'une rubrique \(prise en charge de la touche F1\)  
  
-   Création d'un package de contenu de la marque de visionneuse d'aide  
  
-   Déploiement d'un ensemble d'articles  
  
-   Ajout d'aide à l'interpréteur de commandes de Visual Studio \(intégrée ou isolé\)  
  
-   Ressources supplémentaires  
  
### Création d'une rubrique \(prise en charge de la touche F1\)  
 Cette section fournit une vue d'ensemble des composants d'une rubrique présentée, exigences de rubrique, une brève description de la création d'une rubrique \(y compris les exigences de prise en charge de F1\) et enfin, une rubrique d'exemple avec son résultat.  
  
 **Présentation de rubrique visionneuse de l'aide**  
  
 Lorsqu'une rubrique est appelée pour le rendu, la visionneuse d'aide Obtient les éléments de package personnalisées qui sont associés à la rubrique au moment de l'installation ou de la dernière mise à jour, ainsi que la rubrique XHTML et combine les deux pour provoquer l'affichage du contenu présenté \(données marque \+ données de la rubrique\).  Le package de personnalisation contient des logos, prise en charge des comportements de contenu et le texte de marque \(droits d'auteur, etc.\).  Pour plus d'informations sur les éléments de package de personnalisation, consultez la rubrique Création de la marque « Package » ci\-dessous.  Il est associé à la rubrique aucun package de personnalisation, la visionneuse d'aide utilisera le package de personnalisation secours situé dans la racine de l'application visionneuse d'aide \(Branding\_en\-US.mshc\).  
  
 **Aider les exigences de rubrique visionneuse**  
  
 Pour être rendue correctement dans la visionneuse d'aide, contenu de la rubrique brut doit être XHTML 1.1 base de W3C.  
  
 En règle générale, une rubrique contient deux sections :  
  
-   Métadonnées \(voir le contenu de référence de métadonnées\): ID de nœud, etc. parent pour les données sur le sujet, par exemple, l'ID unique de la rubrique, la valeur de mot clé, l'ID de la table des matières, de la rubrique.  
  
-   Corps de contenu : conforme à XHTML 1.1 de la base W3C qui inclut pris en charge les comportements de contenu \(zone réductible, extrait de code, etc. Une liste complète ci\-dessous\).  
  
 Package de personnalisation de Visual Studio prises en charge des contrôles :  
  
-   Liens  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Membres hérités  
  
-   LanguageSpecificText  
  
 Chaînes de langue prise en charge \(non sensible à la casse\) :  
  
-   JavaScript  
  
-   CSharp ou c\#  
  
-   cplusplus ou Visual c\+\+ ou c \+\+  
  
-   JScript  
  
-   Visual Basic ou Visual Basic  
  
-   f \# ou fsharp ou fs  
  
-   autre – une chaîne qui représente un nom de langue  
  
 **Création d'une rubrique de la visionneuse d'aide**  
  
 Créez un document XHTML nommé ContosoTopic4.htm et inclure la balise de titre \(ci\-dessous\).  
  
```html  
<html> <head> <title>Contoso Topic 4</title> </head> <body> </body> </html>  
  
```  
  
 Ensuite, ajoutez les données permettant de définir comment la rubrique doit être présenté \(self marque ou non\), comment référencer cette rubrique pour F1, où cette rubrique existe dans la table des matières, son ID \(pour la référence de lien par d'autres rubriques\), etc..  Consultez le tableau « Métadonnées de contenu » ci\-dessous pour obtenir la liste complète des métadonnées prises en charge.  
  
-   Dans ce cas, nous allons utiliser notre propre package de personnalisation, une variante du package de personnalisation visionneuse d'aide Visual Studio.  
  
-   Ajoutez le nom de métadonnées de la touche F1 et la valeur \(contenu de « Microsoft.Help.F1 » \= « ContosoTopic4 »\) qui correspondra à la valeur de F1 fournie dans le sac de l'IDE.  \(Voir la section prise en charge de la touche F1 pour plus d'informations\).   C'est la valeur qui correspond à la touche F1 appeler à partir de l'IDE pour afficher cette rubrique quand F1 est choisi dans l'IDE.  
  
-   Ajoutez l'ID de rubrique. Il s'agit de la chaîne qui est utilisée par les autres rubriques à lier à cette rubrique.  Il est l'ID visionneuse d'aide pour cette rubrique.  
  
-   Pour la table des matières, ajoutez le nœud du parent de cette rubrique pour définir l'emplacement de ce nœud de table des matières de rubrique.  
  
-   Pour la table des matières, ajoutez l'ordre des nœuds de cette rubrique. Lorsque le nœud parent possède un nombre n de nœuds enfants, définissez l'ordre des nœuds enfants emplacement de cette rubrique. Par exemple, cette rubrique est numéro 4 de 4 rubriques enfants.\)  
  
 Section de métadonnées d'exemple :  
  
```html  
<html> <head> <title>Contoso Topic 4</title> <meta name="SelfBranded" content="false" /> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> </head> <body> </body> </html>  
  
```  
  
 **Le corps de la rubrique**  
  
 Le corps \(sans l'en\-tête et le pied de page\) de la rubrique contient des liens de page, une section de note, une zone réductible, un extrait de code et une section de texte spécifique du langage.  Consultez la section Personnalisation pour plus d'informations sur les zones de la rubrique présentée.  
  
1.  Ajoutez une balise de titre de rubrique :  `<div class="title">Contoso Topic 4</div>`  
  
2.  Ajoutez une section Remarque : `<div class="alert"> add your table tag and text </div>`  
  
3.  Ajoutez une zone réductible :  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Ajouter un extrait de code :  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Ajouter un texte spécifique code langue :  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Notez que devLangnu \= vous permet d'entrer d'autres langages. Par exemple, devLangnu \= « Fortran » affichera Fortran lorsque l'extrait de code DisplayLanguage \= Fortran  
  
6.  Ajouter des liens de la page : `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Remarque : pour non pris en charge nouveau « langue d'affichage » \(par exemple, F \#, Cobol, Fortran\) la colorisation de code dans l'extrait de code sera monochrome.  
  
 **Rubrique visionneuse d'aide exemple** le code montre comment définir des métadonnées, un extrait de code, une zone réductible et texte en langue spécifique.  
  
```  
<?xml version="1.0" encoding="utf-8"?> <html> <head> <title>Contoso Topic 4</title> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> <meta name="SelfBranded" content="false" /> </head> <body> <div class="title">Contoso Topic 4</div> <div id="header"> <table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%"> <tr id="headerTableRow2"><td align="left"> <span id="nsrTitle">Contoso Topic 1</span> </td> <td align="right"> </td></tr> <tr id="headerTableRow1"><td align="left"> <span id="runningHeaderText">Contoso Widgets & Sprockets</span> </td></tr> </table> </div> <h2>Table of Contents</h2> <ul class="toc"> <li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li> <li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li> </ul> <div class="topic"> <div id="mainSection"> <div id="mainBody"> <a name="introduction"></a> <h2>1.0 Introduction</h2> <p>[This documentation is for sample purposes only.]</p> <p>Contoso Topic 1 contains examples of: <ul> <li>Collapsible Area</li> <li>Bookmark ("See also")</li> <li>Code Snippets from Branding Package</li> </ul> </p> <div class="alert"><table><tr><th> <strong>Note </strong></th></tr> <tr><td> <p>This is an example of a <span class="label">Note </span>section. Call out important items for your reader in this <span class="label">Note </span>box. </p></td></tr> </table> </div> </div> <CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> <a id="sectionToggle0"><!----></a> <div> Example of Collapsible Area <br/> Lorem ipsum dolor sit amet... </div> </CollapsibleArea> <div id="snippetGroup" > <CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" > Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip Dim messageBoxVB as New System.Text.StringBuilder() messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds) messageBoxVB.AppendLine() ... MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event") End Sub </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e) { System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder(); messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds ); messageBoxCS.AppendLine(); ... MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" ); } </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" > some F# code </CodeSnippet> </div> <h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" /> <a name="seealso"></a> <h1 class="heading">See Also</h1> <div id="seeAlsoSection" class="section"> <div class="seeAlsoStyle"> <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a> </div> </div> </div> </div> </body> </html>  
  
```  
  
 **Prise en charge de la touche F1**  
  
 Dans Visual Studio, sélectionnez F1 génère des valeurs fournies à partir de la position du curseur dans l'IDE et remplit un « sac de propriétés » avec les valeurs fournies \(basé sur l'emplacement du curseur. Lorsque le curseur se trouve sur la fonctionnalité x, la fonctionnalité x est actif\/actif dans et remplit le sac de propriétés avec des valeurs.  F1 est le jeu de propriétés est rempli, puis \(F1\) de Visual Studio code vérifie si la source d'aide les clients par défaut est local ou en ligne \(en ligne est la valeur par défaut\), puis crée la chaîne appropriée basée sur les utilisateurs \(en ligne est la valeur par défaut\) – exécution \(voir les paramètres de lancement du Guide Administrateur aide pour un fichier exe\) avec les paramètres de la visionneuse d'aide locale \+ l'ou les mots clés du conteneur de propriétés si l'aide locale est la valeur par défaut , ou l'URL MSDN avec le mot clé dans la liste de paramètres.  
  
 Si trois chaînes sont retournées pour F1, appelée pour sous forme de chaîne à valeurs multiples, prendre le premier terme, recherchez pour effectuer un test, et si trouvé, nous aurons fini ; Si ce n'est pas le cas, passer à la chaîne suivante.  Ordre est important. Présentation des mots clés à valeurs multiples doit être une chaîne la plus longue chaîne plus courte.  Pour cela, dans le cas des mots clés à valeurs multiples, examinez la chaîne d'URL de F1 en ligne, ce qui inclut le mot clé choisi.  
  
 Dans Visual Studio 2012, nous intentionnellement apporté une division renforcée entre en ligne et hors connexion, afin que si le paramètre l'utilisateur était d'en ligne, puis nous avons simplement transmis la demande F1 directement à notre service de requête en ligne sur MSDN, plutôt que de routage via l'Agent de bibliothèque d'aide que nous avions dans Visual Studio 2010. Nous puis repose sur un état de « contenu fournisseur installé \= true » pour déterminer s'il faut faire autre chose dans ce contexte. Si la valeur est true, nous effectuons cette logique d'analyse et de routage en fonction de ce que vous souhaitez prendre en charge pour vos clients. Si la valeur est false, puis nous suffit d'aller sur MSDN. Si le paramètre l'utilisateur est local, tous les appels accédez simplement au moteur d'aide local.  
  
 F1 diagramme de flux :  
  
 ![F1 flow](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 Lorsque la source de contenu d'aide par défaut visionneuse d'aide est définie sur en ligne \(lancement de navigateur\) :  
  
-   Fonctionnalités de Visual Studio partenaire \(VSP\) émettre une valeur pour le jeu de propriétés F1 \(prefix.keyword sac de propriété et en ligne URL pour le préfixe dans le Registre\): F1 envoie une URL VSP \+ paramètres dans le navigateur.  
  
-   Fonctionnalités de Visual Studio \(éditeur de langage, les éléments de menu spécifiques de Visual Studio, etc.\): F1 envoie une URL Visual Studio au navigateur.  
  
 Lorsque la source de contenu d'aide par défaut visionneuse d'aide est définie à l'aide locale \(lancement dans la visionneuse d'aide\) :  
  
-   Fonctionnalités VSP où le mot clé correspondent entre sac F1 et des index de magasin local \(autrement dit, le prefix.keyword du sac de propriété \= valeur trouvée dans l'index de magasin local\): F1 affiche la rubrique de la visionneuse d'aide.  
  
-   Fonctionnalités de Visual Studio \(aucune option pour le VSP remplacer le jeu de propriétés émis à partir des fonctionnalités de Visual Studio\): F1 affiche une rubrique dans la visionneuse d'aide Visual Studio.  
  
 Définissez les valeurs de Registre suivantes pour activer le fournisseur contenu d'aide F1 de secours. F1 secours signifie que la visionneuse d'aide est configurée pour rechercher des F1 Aide en ligne, et le contenu du fournisseur est installé localement pour le disque dur. La visionneuse d'aide doit ressembler à l'aide locale pour le contenu même si le paramètre par défaut est de l'aide en ligne.  
  
1.  Définir le **VendorContent** valeur sous la clé de Registre 2.1 vous aider à :  
  
    -   Pour les systèmes d'exploitation 32 bits :  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         « VendorContent » \= DWORD: 00000001  
  
    -   Pour les systèmes d'exploitation 64 bits :  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         « VendorContent » \= DWORD: 00000001  
  
2.  Enregistrer l'espace de noms partenaire sous la clé de Registre 2.1 vous aider à :  
  
    -   Pour les systèmes d'exploitation 32 bits :  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Partner*\\ \< namespace \>*  
  
         « emplacement » \= « hors connexion »  
  
    -   Pour les systèmes d'exploitation 64 bits :  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Partner*\\ \< namespace \>*  
  
         « emplacement » \= « hors connexion »  
  
 **Analyse de l'espace de noms natif de base**  
  
 Pour activer l'analyse de base espace de noms natif, dans le Registre ajouter une nouvelle valeur de DWORD par le nom de : BaseNativeNamespaces et définissez sa valeur sur 1 \(sous la clé de catalogue qu'ils souhaitent prendre en charge\).  Par exemple, si vous souhaitez utiliser le catalogue de Visual Studio, vous pouvez ajouter la clé pour le chemin d'accès :  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
 Lorsqu'un mot clé F1 dans le format de QU'EN\-TÊTE\/de la méthode est rencontrée, le caractère « \/ » est analysé, ce qui entraîne la construction suivante :  
  
-   EN\-tête : sera l'espace de noms peut être utilisé pour inscrire dans le Registre  
  
-   MÉTHODE : cela deviendra le mot clé qui est transmis via.  
  
 Par exemple, étant donné une bibliothèque personnalisée appelée CustomLibrary et une méthode appelée MyTestMethod, lorsqu'une demande arrive il de F1 seront au format `CustomLibrary/MyTestMethod`.  
  
 Un utilisateur peut inscrire CustomLibrary en tant que l'espace de noms sous la ruche de partenaires puis fournir toute clé emplacement leur choix, et le mot clé transmis à la requête sera MyTestMethod.  
  
 **Activer l'aide de l'outil dans l'IDE de débogage**  
  
 Ajoutez la clé de Registre suivante et la valeur :  
  
 Touche d'aide HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\12.0\\Dynamic : afficher la sortie de débogage dans le prix de vente : Oui  
  
 Dans l'IDE, dans le menu Aide, sélectionnez « Contexte de vous aider à déboguer »  
  
 **Métadonnées de contenu**  
  
 Dans le tableau suivant, une chaîne qui s'affiche entre crochets est un espace réservé qui doit être remplacé par une valeur reconnue. Par exemple, dans \< meta name\="Microsoft.Help.Locale » contenu \= « \[code de langue\] » \/ \>, « \[code de langue\] » doit être remplacé par une valeur comme » en\-us ».  
  
|Propriété \(représentation HTML\)|Description|  
|---------------------------------------|-----------------|  
|\< meta name\="Microsoft.Help.Locale « contenu \="\[langue\-code\]"\/ \>|Définit les paramètres régionaux de cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu'une seule fois et doit être insérée au\-dessus de toutes les autres balises Microsoft Help. Si cette balise n'est pas utilisée, le corps du texte de la rubrique est indexé en utilisant le séparateur de mots qui est associé aux paramètres régionaux du produit, s'il est spécifié ; dans le cas contraire, l'en\-us lexical est utilisé. Cette balise est conforme à la norme RFC 4646 ISOC. Pour vous assurer que Microsoft Help fonctionne correctement, utilisez cette propriété au lieu de l'attribut de langue général.|  
|\< meta name\="Microsoft.Help.TopicLocale « contenu \="\[langue\-code\]"\/ \>|Définit les paramètres régionaux de cette rubrique lorsque d'autres paramètres régionaux est également utilisés. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu'une seule fois. Utilisez cette balise lorsque le catalogue contient du contenu dans plusieurs langues. Plusieurs rubriques dans un catalogue peuvent avoir le même ID, mais chacun doit spécifier une TopicLocale unique. La rubrique qui spécifie un TopicLocale qui correspond aux paramètres régionaux du catalogue est le la rubrique qui s'affiche dans la table des matières. Toutefois, toutes les versions de langue de la rubrique sont affichées dans les résultats de la recherche.|  
|\< title \> \[titre\] \< \/title \>|Spécifie le titre de cette rubrique. Cette balise est requise et doit être utilisée qu'une seule fois dans une rubrique. Si le corps de la rubrique ne contient pas de section title \< div \>, ce titre s'affiche dans la rubrique et dans la table des matières.|  
|\< nom de métadonnées \= « Microsoft.Help.Keywords » contenu \= "\[aKeywordPhrase\]" \/ \>|Spécifie le texte d'un lien qui s'affiche dans le volet de l'index de la visionneuse d'aide. Lorsque l'utilisateur clique sur le lien, la rubrique s'affiche. Vous pouvez spécifier plusieurs mots clés d'index pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que des liens vers cette rubrique apparaissent dans l'index. Mots clés « K » à partir de versions antérieures de l'aide peuvent être convertis en cette propriété.|  
|\< meta name\="Microsoft.Help.Id « contenu \="\[TopicID\]"\/ \>|Définit l'identificateur de cette rubrique. Cette balise est requise et doit être utilisée qu'une seule fois dans une rubrique. L'ID doit être unique parmi les rubriques dans le catalogue qui ont les mêmes paramètres régionaux. Dans une autre rubrique, vous pouvez créer un lien vers cette rubrique à l'aide de ce code.|  
|\< meta name\="Microsoft.Help.F1 « content\="\[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator\]"\/ \>|Spécifie le mot clé F1 pour cette rubrique. Vous pouvez spécifier plusieurs mots clés F1 pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que cette rubrique s'affiche lorsque l'utilisateur d'une application appuie sur la touche F1. En règle générale, qu'un seul mot clé F1 est spécifié pour une rubrique. Mots clés « F » à partir de versions antérieures de l'aide peuvent être convertis en cette propriété.|  
|\< nom de métadonnées \= le contenu de la « Description » \= "\[rubrique description\]" \/ \>|Fournit un bref résumé du contenu de cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu'une seule fois. Cette propriété est accessible directement par la bibliothèque de la requête. Il n'est pas stocké dans le fichier d'index.|  
|\< meta name\="Microsoft.Help.TocParent « contenu \="\[parent\_Id\]"\/ \>|Spécifie la rubrique parente de cette rubrique dans la table des matières. Cette balise est requise et doit être utilisée qu'une seule fois dans une rubrique. La valeur est le Microsoft.Help.Id du parent. Une rubrique peut avoir qu'un seul emplacement dans la table des matières. « \-1 » est considéré comme l'ID de rubrique pour la racine de la table des matières. Dans [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)], que la page est la page d'accueil de visionneuse d'aide. Il s'agit de la même raison que nous ajoutons spécifiquement TocParent \=\-1 pour certaines rubriques pour vous assurer qu'ils apparaissent en haut niveau. Page d'accueil de la visionneuse d'aide est une page de système et donc non remplaçables. Si VSP essaie d'ajouter une page avec un ID de \-1, il peut obtenir ajouté à l'ensemble de contenu, mais visionneuse d'aide sera toujours utiliser la page système – accueil de visionneuse de l'aide|  
|\< meta name\="Microsoft.Help.TocOrder « contenu \="\[entier\]"\/ \>|Spécifie l'emplacement dans la table des matières cette rubrique par rapport à ses sujets homologues. Cette balise est requise et doit être utilisée qu'une seule fois dans une rubrique. La valeur est un entier. Une rubrique qui spécifie un entier de faible valeur s'affiche au\-dessus une rubrique qui spécifie un entier de valeur plus élevée.|  
|\< meta name\="Microsoft.Help.Product « contenu \="\[product code\]"\/ \>|Spécifie le produit décrits dans cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu'une seule fois. Cette information peut également être fournie comme paramètre qui est passé à l'indexeur de l'aide.|  
|\< meta name\="Microsoft.Help.ProductVersion « contenu \="\[version number\]"\/ \>|Spécifie la version du produit décrits dans cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu'une seule fois. Cette information peut également être fournie comme paramètre qui est passé à l'indexeur de l'aide.|  
|\< meta name\="Microsoft.Help.Category « contenu \="\[string\]"\/ \>|Utilisé par les produits pour identifier des sous\-sections de contenu. Vous pouvez identifier plusieurs sous\-sections pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que des liens pour identifier les sous\-sections. Cette balise est utilisée pour stocker les attributs de TargetOS et TargetFrameworkMoniker lorsqu'une rubrique est convertie à partir d'une version antérieure de l'aide. Le format du contenu est AttributeName:AttributeValue.|  
|\< contenu name\="Microsoft.Help.TopicVersion de métadonnées \= « \[rubrique version number\] » \/ \>|Spécifie cette version de la rubrique lorsque plusieurs versions existent dans un catalogue. Microsoft.Help.Id n'est pas garanti pour être unique, cette balise est nécessaire lorsque plusieurs versions d'une rubrique existent dans un catalogue, par exemple, lorsqu'un catalogue contient une rubrique pour le .NET Framework 3.5 et une rubrique pour le .NET Framework 4 et les deux ont le même Microsoft.Help.Id.|  
|\< nom de métadonnées \= le contenu de « SelfBranded » \= "\[vrai ou faux\]" \/ \>|Indique si cette rubrique utilise le package de personnalisation de démarrage de gestionnaire de bibliothèque d'aide ou un package de personnalisation est spécifique à la rubrique. Cette balise doit être TRUE ou FALSE. Si la valeur est TRUE, le package de personnalisation pour la rubrique associée remplace le package de personnalisation est défini au Gestionnaire de bibliothèque d'aide afin que la rubrique est rendue comme prévu même si elle diffère de l'affichage d'un autre contenu. Si la valeur est FALSE, la rubrique actuelle est rendue en fonction du package de personnalisation est défini au démarrage du Gestionnaire de bibliothèque d'aide. Par défaut, le Gestionnaire de bibliothèque d'aide suppose automatique marque sur la valeur false à moins que la variable SelfBranded est déclarée en tant que TRUE ; Par conséquent, vous n'avez pas à déclarer \< nom de métadonnées \= « SelfBranded » content \= « FALSE » \/ \>.|  
  
### Création d'un package de personnalisation  
 La version de Visual Studio comprend un nombre de différents produits Visual Studio, y compris les interpréteurs de commandes intégrés isolé pour partenaires Visual Studio.  Chacun de ces produits nécessite une certaine de contenu d'aide basé sur la rubrique Personnalisation de prise en charge, unique pour le produit.  Par exemple, rubriques Visual Studio besoin d'avoir une présentation cohérente marque, tandis que SQL Studio, qui englobe l'ISO Shell, nécessite son propre contenu unique aide marque pour chaque rubrique.  Un partenaire de Shell intégré souhaiterez peut\-être les rubriques d'aide se trouver dans le contenu d'aide de Visual Studio produit parent tout en conservant leur propre marque de rubrique.  
  
 Personnalisation des packages sont installés par le produit contenant la visionneuse d'aide.  Pour les produits Visual Studio :  
  
-   Un package de personnalisation secours \(.mshc Branding\_ \< locale \>\) est installé à la racine d'application aide les 2.1 visionneuse \(exemple : C:\\Program Files \(x 86\) \\Microsoft Help Viewer\\v2.1\) par le pack de langue visionneuse d'aide.  Il est utilisé pour les cas où le produit marque le package n'est pas installé \(aucun contenu n'a été installé\) ou dans lequel le package de personnalisation installé est endommagé.  Notez que les éléments de Visual Studio \(logo et évaluation\) sont ignorés lorsque le secours racine application personnalisation du package est utilisé.  
  
-   Lorsque le contenu de Visual Studio est installé à partir du service de package de contenu, un package de personnalisation est également installé \(pour le premier scénario d'installation du contenu de temps\).  S'il existe une mise à jour pour le package de personnalisation, la mise à jour est installé lors de la prochaine mise à jour de contenu ou l'action d'installation de package supplémentaire se produit.  
  
 La visionneuse d'aide Microsoft prend en charge la personnalisation des rubriques basées sur les métadonnées de la rubrique.  
  
-   Où les métadonnées de la rubrique définissent self marque \= true, afficher la rubrique étant, ne faites rien \(en ce qui concerne la marque\).  
  
-   Où les métadonnées de la rubrique définissent self marque \= false, utiliser le package de personnalisation associé avec la valeur des métadonnées TopicVendor.  
  
-   Contenu où les métadonnées de la rubrique définissent name\="Microsoft.Help.TopicVendor » \= \< marque nom du package dans le fournisseur MSHA \>, utiliser le package de personnalisation défini dans la valeur de contenu.  
  
-   Notez que, dans le catalogue de Visual Studio, il existe une application de priorité des Packages de personnalisation.  Personnalisation de première Visual Studio par défaut est appliqué et ensuite, si définis dans les métadonnées de la rubrique et la prise en charge avec la personnalisation associée package \(comme défini dans msha de l'installation\), le défini par le fournisseur de personnalisation est appliqué comme un remplacement.  
  
 Éléments de personnalisation se répartissent généralement en trois catégories principales :  
  
-   Éléments d'en\-tête \(exemples lien commentaires conditionnels dédit de responsabilité, logo\)  
  
-   Contenu des comportements \(exemples incluent les éléments de texte de contrôle Développer\/réduire et éléments de l'extrait de code\)  
  
-   Éléments du pied de page \(par exemple, Copyright\)  
  
 Éléments considérés comme incluent des éléments personnalisés \(détaillée dans cette spécification\) :  
  
-   Logo de produit\/du catalogue \(par exemple, Visual Studio\)  
  
-   Éléments de liaison et de courrier électronique des commentaires  
  
-   Dédit de responsabilité  
  
-   Texte de copyright  
  
 Fichiers de prise en charge dans le package de personnalisation de visionneuse d'aide Visual Studio sont les suivantes :  
  
-   Graphiques \(logos, icônes, etc.\).  
  
-   Branding.js – prise en charge des comportements contenus des fichiers de script  
  
-   Branding.XML – chaînes utilisé de manière cohérente sur le contenu du catalogue.  Remarque : pour les éléments de texte de localisation de Visual Studio dans le branding.xml, incluent \_locID \= « \< valeur unique \> »  
  
-   Branding.CSS : les définitions de style pour la cohérence de la présentation  
  
-   Printing.CSS – présentation imprimée cohérent des définitions de style  
  
 Comme indiqué ci\-dessus, les Packages de personnalisation sont associés à la rubrique :  
  
-   Lorsque SelfBranded \= false est défini dans les métadonnées, la rubrique hérite le catalogue de package de personnalisation  
  
-   Ou lorsque SelfBranded \= false et il est un Package de personnalisation unique défini dans le MSHA et disponible lorsque le contenu est installé  
  
 Pour vsp implémentation de packages marque personnalisées \(contenu VSP, SelfBranded \= True\), une façon de procéder consiste à commencer par le package de personnalisation secours \(installé avec la visionneuse d'aide\) et modifier le nom du fichier comme il convient.  Le fichier .mshc Branding\_ \< locale \> est un fichier zip contenant l'extension de fichier passé à .mshc, il vous suffit de modifier l'extension de .mshc par .zip et extraire le contenu.  Voir ci\-dessous pour la personnalisation des éléments du package et de modifier si nécessaire \(par exemple, modifier le logo et le logo VSP la référence pour le logo dans le fichier Branding.xml, mettre à jour Branding.xml par les caractéristiques VSP, etc.\).  
  
 Lorsque toutes les modifications sont effectuées, créez un fichier zip contenant les éléments de personnalisation souhaités et remplacez l'extension .mshc.  
  
 Pour associer le package de personnalisation personnalisé, créez le MSHA qui contient la référence au fichier mshc marque ainsi que le contenu mshc \(qui contient les rubriques\).  Voir ci\-dessous « MSHA » pour la création d'une base MSHA.  
  
 Le fichier Branding.xml contient une utilisée pour le rendu constamment des éléments spécifiques dans une rubrique lorsque cette rubrique contient des éléments de liste \< meta name\="Microsoft.Help.SelfBranded « contenu \="false"\/ \>.  Vous trouverez ci\-dessous la liste des éléments dans le fichier Branding.xml Visual Studio.  Notez que cette liste est destinée à être utilisée comme modèle pour les premiers utilisateurs ISO Shell, où ils modifier ces éléments \(logo, commentaires et droits d'auteur, par exemple\) pour répondre à leur besoins de personnalisation du produit.  
  
 Remarque : les variables indiqués par « {n} » ont des dépendances de code – suppression ou modification de ces valeurs entraîne des erreurs et éventuellement de blocage d'application. Identificateurs de localisation \(exemple \_locID\="codesnippet.n »\) sont inclus dans le Package de personnalisation de Visual Studio.  
  
 **Branding.Xml**  
  
|||  
|-|-|  
|Fonctionnalité :|**CollapsibleArea**|  
|Utilisation :|Développer le texte du contrôle de contenu réduit|  
|**Élément**|**Valeur**|  
|ExpandText|Développer|  
|CollapseText|Réduire|  
|Fonctionnalité :|**CodeSnippet**|  
|Utilisation :|Texte de contrôle l'extrait de code.  Remarque : Contenu d'extrait de Code avec un espace « Sans rupture » est remplacé par espace.|  
|**Élément**|**Valeur**|  
|CopyToClipboard|Copier dans le Presse\-papiers|  
|ViewColorizedText|Afficher avec des couleurs|  
|CombinedVBTabDisplayLanguage|Visual Basic \(exemple\)|  
|VBDeclaration|Déclaration|  
|VBUsage|Utilisation|  
|Fonctionnalité :|**Logo, un pied de page et des commentaires**|  
|Utilisation :|Fournir un contrôle des commentaires client fournir des commentaires sur la rubrique actuelle par courrier électronique.  Texte de copyright pour le contenu.  Définition du logo.|  
|**Élément**|**Valeur \(ces chaînes peuvent être modifiées pour répondre aux besoins des premiers utilisateurs de contenu.\)**|  
|Droits d'auteur|© 2013 Microsoft Corporation. Tous droits réservés.|  
|SendFeedback|\< un href \= "{0}" \\{1\\} \> envoyer des commentaires \< \/a \> sur cette rubrique à Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]|  
|LogoFileName|vs\_logo\_bk.gif|  
|LogoFileNameHC|vs\_logo\_wh.gif|  
|Fonctionnalité :|**Exclusion de responsabilité**|  
|Utilisation :|Le contenu traduit un ensemble de cas exclusions spécifiques pour l'ordinateur.|  
|**Élément**|**Valeur**|  
|MT\_Editable|Cet article a été traduit par un ordinateur. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode d'édition avec le contenu d'origine en anglais en même temps.|  
|MT\_NonEditable|Cet article a été traduit par un ordinateur. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode d'édition avec le contenu d'origine en anglais en même temps.|  
|MT\_QualityEditable|Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode d'édition avec le contenu d'origine en anglais en même temps.|  
|MT\_QualityNonEditable|Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode d'édition avec le contenu d'origine en anglais en même temps.|  
|MT\_BetaContents|Cet article a été traduits pour la version préliminaire. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode d'édition avec le contenu d'origine en anglais en même temps.|  
|MT\_BetaRecycledContents|Cet article a été traduit manuellement pour la version préliminaire. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode d'édition avec le contenu d'origine en anglais en même temps.|  
|Fonctionnalité :|**LinkTable**|  
|Utilisation :|Prise en charge des liens vers les rubriques en ligne|  
|**Élément**|**Valeur**|  
|LinkTableTitle|Table de liens|  
|TopicEnuLinkText|Permet d'afficher la version anglaise \< \/a \> de cette rubrique est disponible sur votre ordinateur.|  
|TopicOnlineLinkText|Afficher cette rubrique \< un href \= "{0}" \\{1\\} \> en ligne \< \/a \>|  
|OnlineText|En ligne|  
|Fonctionnalité :|**Contrôle Audio vidéo**|  
|Utilisation :|Afficher les éléments et le texte pour le contenu vidéo|  
|**Élément**|**Valeur**|  
|MultiMediaNotSupported|Internet Explorer 9 ou version ultérieure doit être installé pour prendre en charge le contenu de {0}.|  
|VideoText|affichage vidéo|  
|Audiotexte|flux de données audio|  
|OnlineVideoLinkText|\< p \> pour afficher la vidéo de cette rubrique, cliquez sur {0} \< un href \= "\\\\ {1\\\\}" \> \\{2\\}here \< \/a \>. \< \/p \>|  
|OnlineAudioLinkText|\< p \> pour écouter l'audio associé à cette rubrique, cliquez sur {0} \< un href \= "\\\\ {1\\\\}" \> \\{2\\}here \< \/a \>. \< \/p \>|  
|Fonctionnalité :|**Contrôle du contenu non installé**|  
|Utilisation :|Éléments de texte \(chaînes\) utilisés pour le rendu de contentnotinstalled.htm|  
|**Élément**|**Valeur**|  
|ContentNotInstalledTitle|Aucun contenu n'a été trouvé sur votre ordinateur.|  
|ContentNotInstalledDownloadContentText|\< p \> pour télécharger du contenu sur votre ordinateur, \< un href \= "{0}" \\{1\\} \> cliquez sur l'onglet gérer \< \/a \>. \< \/p \>|  
|ContentNotInstalledText|\< p \> pas de contenu est installé sur votre ordinateur. Consultez votre administrateur local aide contenu installation. \< \/p \>|  
|Fonctionnalité :|**Contrôle de rubrique introuvable**|  
|Utilisation :|Éléments de texte \(chaînes\) utilisés pour le rendu de topicnotfound.htm|  
|**Élément**|**Valeur**|  
|TopicNotFoundTitle|Impossible de trouver la rubrique demandée sur votre ordinateur.|  
|TopicNotFoundViewOnlineText|\< p \> la rubrique que vous avez demandée est introuvable sur votre ordinateur, mais vous pouvez \< un href \= "{0}" \\{1\\} \> Afficher la rubrique en ligne \< \/a \>. \< \/p \>|  
|TopicNotFoundDownloadContentText|\< p \> consultez le volet de navigation pour obtenir des liens vers des rubriques similaires, ou \< un href \= "{0}" \\{1\\} \> cliquez sur l'onglet gérer \< \/a \> pour télécharger du contenu sur votre ordinateur. \< \/p \>|  
|TopicNotFoundText|\< p \> la rubrique que vous avez demandée est introuvable sur votre ordinateur. \< \/p \>|  
|Fonctionnalité :|**Rubrique endommagé contrôle**|  
|Utilisation :|Éléments de texte \(chaînes\) utilisés pour le rendu de topiccorrupted.htm|  
|**Élément**|**Valeur**|  
|TopicCorruptedTitle|Impossible d'afficher la rubrique demandée.|  
|TopicCorruptedViewOnlineText|\< p \> visionneuse d'aide ne peut pas afficher la rubrique demandée. Il peut y avoir une erreur dans le contenu de la rubrique ou une dépendance de système sous\-jacent. \< \/p \>|  
|Fonctionnalité :|**Contrôle de la Page d'accueil**|  
|Utilisation :|Texte prenant en charge l'affichage du contenu du nœud de niveau supérieur de visionneuse d'aide.|  
|**Élément**|**Valeur**|  
|HomePageTitle|Accueil de visionneuse d'aide|  
|HomePageIntroduction|\< p \> Bienvenue dans la visionneuse d'aide Microsoft, une source incontournable d'informations pour toute personne qui utilise les outils, produits, technologies et services Microsoft. La visionneuse d'aide vous donne accès aux informations de référence et de procédure, exemple de code, articles techniques et bien plus encore. Pour trouver le contenu que vous avez besoin, parcourez la table des matières, utilisez la recherche en texte intégral, ou parcourez le contenu à l'aide du mot clé index. \< \/p \>|  
|HomePageContentInstallText|\< p \>\< br \/ \> Utilisez le \< un href \= "{0}" \\{1\\} \> onglet gérer le contenu \< \/a \> pour effectuer les opérations suivantes : contenu \< ul \>\< li \> ajouter à votre ordinateur. \< \/li \>\< li \> Vérification des mises à jour pour votre contenu local. \< \/li \>\< li \> Supprimer du contenu de votre ordinateur. \< \/li \>\< \/ul \>\< \/p \>|  
|HomePageInstalledBooks|Livres installés|  
|HomePageNoBooksInstalled|Aucun contenu n'a été trouvé sur votre ordinateur.|  
|HomePageHelpSettings|Paramètres de contenu d'aide|  
|HomePageHelpSettingsText|\< p \> votre paramètre actuel est l'aide locale. La visionneuse d'aide affiche le contenu que vous avez installés sur votre ordinateur. \< br \/ \> pour modifier votre source de contenu de l'aide sur la barre de menus de Visual Studio, cliquez sur \< span style \= « {0} » \> aide, définir les préférences pour vous aider à \< \/span \>. \< br \/ \>\< \/p \>|  
|Mégaoctets|MO|  
  
 **branding.js**  
  
 Le fichier branding.js contient JavaScript utilisée par les éléments de personnalisation de visionneuse d'aide Visual Studio.  Voici une liste des éléments de personnalisation et de la fonction JavaScript de prise en charge.  Toutes les chaînes à localiser ce fichier sont définies dans la section « Chaînes localisables » en haut de ce fichier.  Notez que les fichiers ICL a été créé pour la localisation des chaînes dans le fichier branding.js.  
  
||||  
|-|-|-|  
|**Fonctionnalité de personnalisation**|**Fonction JavaScript**|**Description**|  
|Var...||Définir des variables|  
|Obtenir le langage de code utilisateur|setUserPreferenceLang|mappe un index \# en langage de code|  
|Définir et obtenir des valeurs de cookies|getCookie, setCookie||  
|Membres hérités|changeMembersLabel|Développer\/réduire un membre hérité|  
|Lorsque SelfBranded \= False|onLoad|Lire la chaîne de requête pour vérifier s'il s'agit d'une demande d'impression.  Définissez tous les codesnippets concentrer l'onglet par défaut de l'utilisateur.  S'il s'agit d'une impression demande puis définissez isPrinterFriendly sur true. Vérifier le mode de contraste élevé.|  
|Extrait de code|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Onglet||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|écrire tous les objets du contrôle réductible dans la liste.|  
||CA\_Click|en fonction de l'état de la zone réductible, définit quelle image et le texte à présenter|  
|Prise en charge du contraste de Logo|isBlackBackground\(\)|Appelée pour déterminer si l'arrière\-plan est noir.  Précise uniquement lorsque le mode de contraste élevé.|  
||isHighContrast\(\)|utiliser un intervalle de couleur pour détecter le mode de contraste élevé|  
||onHighContrast\(black\)|Appelé lorsque le contraste élevé est détecté.|  
|Fonctionnalités LST|||  
||addToLanSpecTextIdSet\(id\)||  
||updateLST\(currentLang\)||  
||getDevLangFromCodeSnippet\(lang\)||  
|Fonctionnalités multimédia|légende \(début, fin, texte, le style\)||  
||findAllMediaControls\(normalizedId\)||  
||getActivePlayer\(normalizedId\)||  
||captionsOnOff\(id\)||  
||toSeconds\(t\)||  
||getAllComments\(node\)||  
||styleRectify \(styleName, styleValue\)||  
||showCC\(id\)||  
||Subtitle\(ID\)||  
  
 **FICHIERS HTM**  
  
 Le package de personnalisation contient un ensemble de fichiers HTM qui prennent en charge des scénarios pour communiquer des informations de clé pour les utilisateurs de contenu d'aide, par exemple une page d'accueil qui contient une section décrivant les ensembles de contenu sont installés et les pages qui informe l'utilisateur lorsque les rubriques est introuvable dans l'ensemble de rubriques local. Notez que ces fichiers HTM peuvent être modifiées par produit.  Fournisseurs de ISO Shell sont en mesure de prendre le package de personnalisation par défaut et modifier le comportement et le contenu de ces pages à la suite de leurs besoins.  Ces fichiers font référence à leur package respectif de personnalisation dans l'ordre des balises personnalisées obtenir le contenu correspondant à partir du fichier branding.xml.  
  
||||  
|-|-|-|  
|**Fichier**|**Utilisation**|**Affiche la Source de contenu**|  
|homepage.htm|Il s'agit d'une page qui affiche le contenu actuellement installé et tout autre message appropriée à présenter à l'utilisateur sur leur contenu.  Ce fichier contient le contenu « Microsoft.Help.Id » de l'attribut de données supplémentaire meta \= « \-1 » qui place ce contenu en haut de la table des matières de contenu local.||  
||\< META\_HOME\_PAGE\_TITLE\_ADD \/ \>|Branding.XML, la balise \< HomePageTitle \>|  
||\< HOME\_PAGE\_INTRODUCTION\_SECTION\_ADD \/ \>|Branding.XML, la balise \< HomePageIntroduction \>|  
||\< HOME\_PAGE\_CONTENT\_INSTALL\_SECTION\_ADD \/ \>|Branding.XML, la balise \< HomePageContentInstallText \>|  
||\< HOME\_PAGE\_BOOKS\_INSTALLED\_SECTION\_ADD \/ \>|Titre de section Branding.xml balise \< HomePageInstalledBooks \>, les données générées à partir de l'application, \< HomePageNoBooksInstalled \> lorsque aucune documentation n'est installée.|  
||\< HOME\_PAGE\_SETTINGS\_SECTION\_ADD \/ \>|Titre de section Branding.xml balise \< HomePageHelpSettings \>, le texte de section \< HomePageHelpSettingsText \>.|  
|topiccorrupted.htm|Lorsqu'il existe une rubrique dans le jeu local, mais pour une raison quelconque ne peut pas être affichée \(endommagé contenu\).||  
||\< META\_TOPIC\_CORRUPTED\_TITLE\_ADD \/ \>|Branding.XML, la balise \< TopicCorruptedTitle \>|  
||\< TOPIC\_CORRUPTED\_SECTION\_ADD \/ \>|Branding.XML, la balise \< TopicCorruptedViewOnlineText \>|  
|topicnotfound.htm|Lorsqu'une rubrique est introuvable dans le contenu local défini ni disponible en ligne||  
||\< META\_TOPIC\_NOT\_FOUND\_TITLE\_ADD \/ \>|Branding.XML, la balise \< TopicNotFoundTitle \>|  
||\< META\_TOPIC\_NOT\_FOUND\_ID\_ADD \/ \>|Branding.XML, la balise \< TopicNotFoundViewOnlineText \> \+ \< TopicNotFoundDownloadContentText \>|  
||\< TOPIC\_NOT\_FOUND\_SECTION\_ADD \/ \>|Branding.XML, la balise \< TopicNotFoundText \>|  
|contentnotinstalled.htm|Lorsque aucun contenu local installé pour le produit.||  
||\< META\_CONTENT\_NOT\_INSTALLED\_TITLE\_ADD \/ \>|Branding.XML, la balise \< ContentNotInstalledTitle \>|  
||\< META\_CONTENT\_NOT\_INSTALLED\_ID\_ADD \/ \>|Branding.XML, la balise \< ContentNotInstalledDownloadContentText \>|  
||\< CONTENT\_NOT\_INSTALLED\_SECTION\_ADD \/ \>|Branding.XML, la balise \< ContentNotInstalledText \>|  
  
 **Fichiers CSS**  
  
 Le Package Visual Studio aide visionneuse marque contient deux fichiers css pour prendre en charge la présentation du contenu cohérente aide de Visual Studio :  
  
-   Branding.CSS – contient des éléments css pour le rendu where SelfBranded \= false  
  
-   Printer.CSS – contient des éléments css pour le rendu where SelfBranded \= false  
  
 Les fichiers branding.CSS inclut des définitions pour la présentation de rubrique Visual Studio \(inconvénient est que le branding.css contenus dans le .mshc Branding\_ \< locale \> à partir du service de package peuvent changer\).  
  
 **Fichiers graphiques**  
  
 Contenu de Visual Studio affiche un logo de Visual Studio ainsi que d'autres graphiques.  Vous trouverez ci\-dessous la liste complète des fichiers graphiques dans le package de personnalisation de visionneuse d'aide Visual Studio.  
  
||||  
|-|-|-|  
|**Fichier**|**Utilisation**|**Exemples**|  
|Clear.gif|Utilisé pour afficher la zone réductible||  
|footer\_slice.gif|Présentation de pied de page||  
|info\_icon.gif|Utilisé lors de l'affichage d'informations|Exclusion de responsabilité|  
|online\_icon.gif|Cette icône est à associer à des liens en ligne||  
|tabLeftBD.gif|Utilisé pour afficher le conteneur d'extrait de code||  
|tabRightBD.gif|Utilisé pour afficher le conteneur d'extrait de code||  
|vs\_logo\_bk.gif|Utilisé pour les références de logo contraste normal tel que défini dans la balise Branding.xml \< LogoFileName \>.  Pour les produits Visual Studio, nom du logo est vs\_logo\_bk.gif.||  
|vs\_logo\_wh.gif|Utilisé pour les références de logo élevé normal tel que défini dans la balise Branding.xml \< LogoFileNameHC \>.  Pour les produits Visual Studio, nom du logo est vs\_logo\_wh.gif.||  
|ccOff.png|Graphique de sous\-titrage||  
|ccOn.png|Graphique de sous\-titrage||  
|ImageSprite.png|Utilisé pour afficher la zone réductible|développer ou réduire le graphique|  
  
### Déploiement d'un ensemble de rubriques  
 Il s'agit d'un didacticiel très simple et rapide pour la création d'un visionneuse de l'aide du déploiement de contenu défini composé d'un fichier MSHA et l'ensemble de fichiers CAB ou MSHC qui contient les rubriques. Le MSHA est un fichier XML qui décrit un ensemble de fichiers CAB ou les fichiers MSHC. La visionneuse d'aide peut lire le MSHA pour obtenir une liste de contenu \(le fichier. CAB ou. Fichiers MSHC\) disponibles pour une installation locale.  
  
 Il s'agit uniquement une introduction décrivant le schéma XML très basique pour la MSHA Observateur d'aide.  Notez qu'il existe un exemple d'implémentation sous cette brève présentation et d'échantillonnage helpcontentsetup.msha.  
  
 Le nom de le MSHA, dans le cadre de cette introduction, est helpcontentsetup.msha \(le nom du fichier peut être n'importe quoi, avec l'extension. MSHA\). Helpcontentsetup.msha \(exemple ci\-dessous\) doit contenir une liste des fichiers CAB MSHCs disponibles.  Notez que le type de fichier doit être cohérent avec la MSHA \(ne prend pas en charge une combinaison de types de fichiers MSHA et CAB\). Pour chaque fichier CAB ou MSHC, il doit y avoir un \< div classe \= « package » \>... \< \/ div \> \(voir l'exemple ci\-dessous\).  
  
 Remarque : dans l'exemple d'implémentation ci\-dessous, nous avons inclus le package de personnalisation. Il est essentiel d'inclure afin d'obtenir les éléments de rendu de contenu Visual Studio nécessaires et les comportements de contenu.  
  
 Exemple de fichier helpcontentsetup.msha: \(remplacez « contenu jeu nom 1 » et « contenu jeu nom 2 », etc. avec les noms des fichiers.\)  
  
```  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div>.  
  
```  
  
1.  Créez un dossier local, quelque chose comme « C:\\SampleContent »  
  
2.  Pour cet exemple, nous allons utiliser les fichiers MSHC pour contenir les rubriques.  Un MSHC est un fichier zip avec l'extension de fichier a été remplacée par .zip à. MSHC.  
  
3.  Créer le ci\-dessous helpcontentsetup.msha sous forme de fichier texte \(le bloc\-notes a été utilisé pour créer le fichier\) et enregistrez\-le dans le dossier indiqué ci\-dessus \(voir l'étape 1\).  
  
 Notez que la classe « Branding » existe et est unique. La personnalisation mshc est inclus dans cette introduction afin que le contenu installé sera la marque, et les comportements de contenu qui sont contenus dans les MSHCs aura les éléments de prise en charge dans le package de personnalisation. Sans cela, les erreurs entraînent lorsque le système de recherche pour les éléments de prise en charge qui ne font pas partie des extraits \(installé\) le contenu.  
  
 Pour obtenir Visual Studio marque le package, copiez fichier Branding\_en\-US.mshc à C:\\Program Files \(x 86\) \\Microsoft Help Viewer\\v2.1\\ dans votre dossier de travail.  
  
```html  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div> <div class="package"> <span class="packageType">branding</span> <span class="name">Branding_en-US</span> <span class="deployed">True</span> <a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a> </div> </div> </body> </html>  
  
```  
  
 **Résumé**  
  
 Utilisation et extension de la procédure ci\-dessus activera vsp déployer leurs ensembles de contenu pour la visionneuse d'aide Visual Studio.  
  
### Ajout de l'aide de Visual Studio Shell \(intégré et isolé\)  
 **Introduction**  
  
 Cette procédure pas à pas montre comment incorporer le contenu d'aide dans une application de Shell Visual Studio, puis le déployer.  
  
 **Spécifications**  
  
1.  [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 isolé Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **Vue d'ensemble**  
  
 Le [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell est une version de la [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] IDE sur lesquels vous pouvez baser une application. Ces applications contiennent le Shell isolé avec des extensions que vous créez. Utiliser des modèles de projet Shell isolé, qui sont inclus dans le [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Kit de développement logiciel, de générer des extensions.  
  
 Les étapes de base pour la création d'une application basée sur le Shell isolé et son aide :  
  
1.  Obtenir le [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] redistribuable du Shell ISO \(téléchargement Microsoft\).  
  
2.  Dans Visual Studio, créez une extension d'aide qui est basée sur l'interpréteur de commandes isolé, par exemple, l'extension de Contoso aide qui est décrit plus loin dans cette procédure pas à pas.  
  
3.  Encapsuler l'extension et l'interpréteur de commandes ISO redistribuable dans un déploiement MSI \(une installation de l'application\). Cette procédure pas à pas n'inclut pas d'une étape de configuration.  
  
 Création d'un magasin de contenu Visual Studio. Pour le scénario d'interpréteur de commandes intégré, modifiez Visual Studio12 au nom du catalogue de produit comme suit :  
  
-   Créez le dossier C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12.  
  
-   Créez un fichier nommé que CatalogType.xml et ajoutez\-le au dossier. Le fichier doit contenir les lignes de code suivantes :  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
 Définir le magasin de contenu dans le Registre. Pour l'environnement intégré, modifiez le nom du catalogue produit VisualStudio12 :  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
     Clé : Valeur la chaîne de LocationPath : C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12\\en\-US  
  
     Clé : Valeur la chaîne de nom de catalogue : [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Documentation  
  
 **Créer le projet**  
  
 Pour créer une extension de Shell isolé :  
  
1.  Dans Visual Studio, sous **fichier**, choisissez **Nouveau projet**, sous **autres Types de projets** choisissez **extensibilité**, puis choisissez  **Visual Studio Shell isolé**. Nommez le projet `ContosoHelpShell`\) pour créer un projet d'extensibilité basé sur le modèle de Shell isolé Visual Studio.  
  
2.  Dans l'Explorateur de solutions, dans le projet ContosoHelpShellUI, dans le dossier de fichiers de ressources, ouvrez ApplicationCommands.vsct. Assurez\-vous que cette ligne est commentée \(recherchez « No\_Help »\) : `<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  Appuyez sur la touche F5 pour compiler et exécuter **Debug**. Dans l'instance expérimentale de l'IDE de Shell isolé, choisissez le **aide** menu. Assurez\-vous que le **Afficher l'aide**, **Ajouter et supprimer le contenu d'aide**, et **définir les préférences pour vous aider à** les commandes s'affichent.  
  
4.  Dans l'Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier de personnalisation du Shell, ouvrez ContosoHelpShell.pkgdef. Pour définir le catalogue d'aide de Contoso, ajoutez les lignes suivantes :  
  
    ```  
    [$RootKey$\Help] "Product"="Contoso" "Catalog"="Contoso" “Version"="100" "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  Dans l'Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier de personnalisation du Shell, ouvrez ContosoHelpShell.Application.pkgdef. Pour activer la touche F1, ajoutez les lignes suivantes :  
  
    ```  
    // F1 Help Provider [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="13407" "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}" @="Help3 Provider" [$RootKey$\HelpProviders] @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}" [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="Help3 Provider" @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  Dans l'Explorateur de solutions, dans le menu contextuel de la solution ContosoHelpShell, choisissez le **propriétés** élément de menu. Sous **Propriétés de Configuration**, sélectionnez **Configuration Manager**. Dans le **Configuration** colonne, remplacez toutes les valeurs « Debug » par « Version ».  
  
7.  Générez la solution. Cela crée un ensemble de fichiers dans un dossier de publication, qui sera utilisé dans la section suivante.  
  
 Pour effectuer ce test car si déployé :  
  
1.  Sur l'ordinateur que vous déployez Contoso pour installer téléchargé ISO Shell \(dessus\).  
  
2.  Créez un dossier dans \\\\Program Files \(x 86\) \\ et nommez\-le `Contoso`.  
  
3.  Copiez le contenu du dossier de publication ContosoHelpShell au dossier de \\Contoso\\ \\\\Program Files \(x 86\).  
  
4.  Démarrez l'Éditeur du Registre en choisissant  **exécuter** dans les **Démarrer** menu et en entrant `Regedit`. Dans l'Éditeur du Registre, sélectionnez **fichier**, puis **Import**. Accédez au dossier de projet ContosoHelpShell. Dans le sous\-dossier ContosoHelpShell, choisissez ContosoHelpShell.reg.  
  
5.  Créer un magasin de contenu :  
  
     Pour le Shell ISO \- création d'un magasin de contenu Contoso C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\ContosoDev12  
  
     Pour [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] un environnement intégré, créez le dossier C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12  
  
6.  Créer que CatalogType.xml et l'ajouter au magasin de contenu \(étape précédente\) :  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Ajoutez les clés de Registre suivantes :  
  
     HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12Key : Valeur de chaîne de LocationPath :  
  
     Pour le Shell ISO :  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell intégré :  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\\\en\-US  
  
     Clé : Valeur la chaîne de nom de catalogue : [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Documentation. Pour ISO Shell, ceci est le nom de votre catalogue.  
  
8.  Copiez votre contenu \(fichiers CAB ou MSHC et MSHA\) vers un dossier local.  
  
9. Exemple la ligne de commande Shell intégré pour le test du magasin de contenu. Pour le Shell ISO, modifier les valeurs de catalogue et launchingApp comme il convient de faire correspondre le produit.  
  
     « C:\\Program Files \(x 86\) \\Microsoft Help Viewer\\v2.1\\HlpViewer.exe » \/catalogName VisualStudio12 \/helpQuery méthode \= « page & id \= ContosoTopic0 » \/launchingApp Microsoft, VisualStudio, 12.0  
  
10. Lancez l'application Contoso \(à partir de la racine d'application Contoso\). ISO Shell, choisissez le **aide** élément de menu, puis réglez le **définir les préférences pour vous aider à** à **utilisation de l'aide locale**.  
  
11. Dans l'interpréteur de commandes, cliquez sur le **aide** élément de menu, puis **Afficher l'aide**. Doit se lancer la visionneuse d'aide locale. Choisissez l'onglet **Gérer le contenu**. Sous **Source d'Installation**, choisissez le **disque** case d'option. Choisissez le **...** bouton et accédez au dossier local contenant le contenu de Contoso \(copié dans le dossier local dans l'étape ci\-dessus\). Choisissez le helpcontentsetup.msha. Contoso doit maintenant s'afficher sous forme de livre dans les sélections de livre. Choisissez **Ajouter**, puis choisissez le **mise à jour** bouton \(coin inférieur droit\).  
  
12. Dans l'IDE de Contoso, appuyez sur la touche F1 pour tester la fonctionnalité de la touche F1.  
  
### Ressources supplémentaires  
 Pour l'API du Runtime, consultez [API d'aide Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
 Pour plus d'informations sur la façon de tirer parti de l'API d'aide, consultez [aide des exemples de Code visionneuse](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 Pour fournir des commentaires sur ces composants, utilisez [Microsoft Connect](http://connect.microsoft.com/).  
  
 Veuillez envoyer vos suggestions de fonctionnalité à [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 Pour obtenir une aide supplémentaire, essayez le [système d'aide et de Documentation pour développeurs MSDN forums](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 Mises à jour importantes de problème, veuillez consulter la [Lisezmoi de visionneuse aide](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 Pour contacter directement l'équipe PM de visionneuse aide, envoyer un courrier électronique à hlpfdbk@microsoft.com