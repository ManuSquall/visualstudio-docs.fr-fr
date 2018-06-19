---
title: Kit de développement logiciel de Microsoft Help Viewer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ddc23ab56df017ef0a37c56cd5b0a81ee33a07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135409"
---
# <a name="microsoft-help-viewer-sdk"></a>Kit de développement logiciel de Microsoft Help Viewer
Cet article contient les tâches suivantes pour les intégrateurs de la visionneuse d’aide Visual Studio :  
  
-   Création d’une rubrique (prise en charge de la touche F1)  
  
-   Création d’un package de marque de contenu de la visionneuse d’aide  
  
-   Déploiement d’un ensemble d’articles  
  
-   Ajout d’aide à l’interpréteur de commandes de Visual Studio (intégré ou isolé)  
  
-   Ressources supplémentaires  
  
### <a name="creating-a-topic-f1-support"></a>Création d’une rubrique (prise en charge de la touche F1)  
Cette section fournit une vue d’ensemble des composants d’une rubrique présentée, les exigences de la rubrique, une brève description de la création d’une rubrique (y compris les exigences de prise en charge de F1) et pour finir, une rubrique d’exemple avec son résultat du rendu.  
  
**Présentation de rubrique de visionneuse de l’aide**  
  
Lorsqu’une rubrique est appelée pour le rendu, la visionneuse d’aide Obtient les éléments de package de marque qui sont associés à la rubrique au moment de l’installation ou de la dernière mise à jour, ainsi que la rubrique XHTML et combine les deux pour entraîner l’affichage du contenu présenté (marque les données + données de la rubrique).  Le package de personnalisation contient des logos, prise en charge des comportements de contenu et le texte de personnalisation (droits d’auteur, etc.).  Pour plus d’informations sur les éléments de package de marque, voir « Création de Package de personnalisation » ci-dessous.  Il est associé à la rubrique aucun package de personnalisation, la visionneuse d’aide utilisera le package de marque secours situé dans la racine de l’application visionneuse d’aide (Branding_en-US.mshc).  
  
**Aider les exigences de rubrique de visionneuse**  
  
Pour s’afficher correctement dans la visionneuse d’aide, le contenu de la rubrique brut doit être XHTML 1.1 de la base W3C.  
  
En règle générale, une rubrique contient deux sections :  
  
-   Métadonnées (voir le contenu de référence de métadonnées) : ID de nœud, etc. parent pour les données sur ce sujet, par exemple, l’ID unique de la rubrique, valeur de mot clé, l’ID de la table des matières, de la rubrique.  
  
-   Corps de contenu : conforme à XHTML 1.1 de la base W3C qui inclut la prise en charge les comportements de contenu (zone réductible, extrait de code, etc. Une liste complète est indiquée ci-dessous).  
  
Package de personnalisation de Visual Studio prises en charge les contrôles :  
  
-   Liens  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Membre hérité  
  
-   LanguageSpecificText  
  
Chaînes de langue prise en charge (non sensible à la casse) :  
  
-   JavaScript  
  
-   CSharp ou c#  
  
-   cplusplus ou visualc ++ ou c ++  
  
-   JScript  
  
-   Visual Basic ou Visual Basic  
  
-   f # ou fsharp ou fs  
  
-   autre - chaîne qui représente un nom de langue  
  
**Création d’une rubrique de la visionneuse d’aide**  
  
Créer un nouveau document XHTML nommé ContosoTopic4.htm et inclure la balise de titre (ci-dessous).  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
Ensuite, ajoutez des données pour définir comment la rubrique doit être présenté (self marque ou non), de la référencer cette rubrique pour F1, dans lequel cette rubrique existe dans la table des matières, son ID (pour la référence de lien par d’autres rubriques), etc.  Consultez le tableau « Métadonnées de contenu » ci-dessous pour obtenir la liste complète des métadonnées prises en charge.  
  
-   Dans ce cas, nous allons utiliser notre propre package de personnalisation, une variante du package de marque de visionneuse d’aide Visual Studio.  
  
-   Ajouter le nom de métadonnées de la touche F1 et la valeur (contenu de « Microsoft.Help.F1 » = « ContosoTopic4 ») qui correspondra à la valeur de F1 fournie dans le jeu de propriétés IDE.  (Voir la section prise en charge de la touche F1 pour plus d’informations.)   C’est la valeur mise en correspondance avec la touche F1 appeler à partir de l’IDE pour afficher cette rubrique quand F1 est choisi dans l’IDE.  
  
-   Ajoutez l’ID de rubrique. Il s’agit de la chaîne qui est utilisée par les autres rubriques à lier à cette rubrique.  Il est l’ID visionneuse d’aide pour cette rubrique.  
  
-   Pour la table des matières, ajoutez le nœud du parent de cette rubrique pour définir l’emplacement de ce nœud de table des matières de rubrique.  
  
-   Pour la table des matières, ajoutez l’ordre des nœuds de cette rubrique. Lorsque le nœud parent possède un nombre n de nœuds enfants, définir l’ordre des nœuds enfants les emplacement de cette rubrique. Par exemple, cette rubrique est numéro 4 de 4 rubriques enfants.)  
  
Section de métadonnées d’exemple :  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
<meta name="SelfBranded" content="false" />     
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
**Le corps de la rubrique**  
  
Le corps (y compris ne pas l’en-tête et le pied de page) de la rubrique contient des liens de page, une section de note, une zone réductible, un extrait de code et une section de texte spécifique de langage.  Consultez la section Personnalisation pour plus d’informations sur les zones de la rubrique présentée.  
  
1.  Ajoutez une balise de titre de rubrique :  `<div class="title">Contoso Topic 4</div>`  
  
2.  Ajoutez une section Remarque : `<div class="alert"> add your table tag and text </div>`  
  
3.  Ajoutez une zone réductible :  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Ajoutez un extrait de code :  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Ajouter du texte spécifique de langage de code : `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Notez que devLangnu = vous permet d’entrer d’autres langages. Par exemple, devLangnu = « Fortran » affichera Fortran lors de l’extrait de code DisplayLanguage = Fortran  
  
6.  Ajouter des liens de la page : `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Remarque : pour non pris en charge nouvelle « langue d’affichage » (par exemple, F #, Cobol, Fortran) la colorisation de code dans l’extrait de code sera monochrome.  
  
**Rubrique visionneuse d’aide exemple** le code illustre comment définir des métadonnées, un extrait de code, une zone réductible et texte de langage spécifique.  
  
```html
<?xml version="1.0" encoding="utf-8"?>  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
<meta name="SelfBranded" content="false" />     
</head>  
  
<body>  
<div class="title">Contoso Topic 4</div>  
  
  <div id="header">  
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">  
        <tr id="headerTableRow2"><td align="left">  
            <span id="nsrTitle">Contoso Topic 1</span>  
          </td>  
<td align="right">  
</td></tr>  
<tr id="headerTableRow1"><td align="left">  
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>  
          </td></tr>  
      </table>  
</div>  
  
<h2>Table of Contents</h2>  
  
<ul class="toc">  
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>  
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>  
</ul>  
  
<div class="topic">  
  
<div id="mainSection">  
<div id="mainBody">  
  
<a name="introduction"></a>  
<h2>1.0 Introduction</h2>  
<p>[This documentation is for sample purposes only.]</p>  
  
<p>Contoso Topic 1 contains examples of:  
<ul>  
<li>Collapsible Area</li>  
<li>Bookmark ("See also")</li>  
<li>Code Snippets from Branding Package</li>  
</ul>  
 </p>  
<div class="alert"><table><tr><th>  
<strong>Note </strong></th></tr>  
<tr><td>  
<p>This is an example of a <span class="label">Note </span>section.    
Call out important items for your reader in this <span class="label">Note </span>box.  
</p></td></tr>  
</table>  
</div>  
</div>  
  
<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">  
  
            <a id="sectionToggle0"><!----></a>  
  
<div>  
Example of Collapsible Area  
<br/>  
Lorem ipsum dolor sit amet...  
</div>  
</CollapsibleArea>  
  
<div id="snippetGroup" >  
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >  
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip  
Dim messageBoxVB as New System.Text.StringBuilder()  
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)  
    messageBoxVB.AppendLine()  
 ...  
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")  
End Sub  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >  
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)   
{   
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();  
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );  
messageBoxCS.AppendLine();  
...  
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );  
}  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >  
some F# code  
</CodeSnippet>  
</div>  
  
<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />  
  
<a name="seealso"></a>  
<h1 class="heading">See Also</h1>  
  
    <div id="seeAlsoSection" class="section">   
    <div class="seeAlsoStyle">  
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Prise en charge de la touche F1**  
  
Dans Visual Studio, en sélectionnant F1 génère des valeurs fournies à partir de l’emplacement du curseur dans l’IDE et remplit un « jeu de propriétés » avec les valeurs fournies (basé sur l’emplacement du curseur. Lorsque le curseur se trouve au-dessus de la fonctionnalité x, la fonctionnalité x est active/de focus et remplit le sac de propriétés avec des valeurs.  Lors de la touche F1 est sélectionné le sac de propriétés est rempli et (F1) de Visual Studio code vérifie si la source d’aide les clients par défaut est local ou en ligne (en ligne est la valeur par défaut), puis crée la chaîne appropriée basée sur les utilisateurs (en ligne est la valeur par défaut) - d’exécution (voir les paramètres de lancement du Guide de l’administrateur aide pour exe) avec les paramètres de la visionneuse d’aide locale + ou les mots clés du jeu de propriétés si aide locale est la valeur par défaut, ou l’URL MSDN avec le mot clé dans la liste de paramètres.  
  
Si trois chaînes sont retournées pour F1, appelée prenne sous forme de chaîne à valeurs multiples, le premier terme, recherchez pour effectuer un test, et si trouvé, nous avons terminé ; Si ce n’est pas le cas, passer à la chaîne suivante.  Ordre est important. Présentation des mots clés à valeurs multiples doit être la chaîne la plus longue à la chaîne la plus courte.  Pour vérifier cela dans le cas pour les mots clés des valeurs multiples, recherchez la chaîne d’URL de F1 en ligne, ce qui inclut le mot clé choisi.  
  
Dans Visual Studio 2012, nous avons intentionnellement apporté une division plus forte entre en ligne et hors connexion, afin que si le paramètre de l’utilisateur a été d’en ligne, puis nous simplement transmis la demande F1 directement à notre service de requête en ligne sur MSDN, plutôt que de routage via l’Agent de bibliothèque d’aide que nous avons dû dans Visual Studio 2010. Nous avons ensuite s’appuient sur un état de « contenu fournisseur installé = true » pour déterminer s’il faut faire autre chose dans ce contexte. Si la valeur est true, nous effectuons cette logique de routage et d’analyse en fonction de ce que vous souhaitez prendre en charge pour vos clients. Si la valeur est false, puis nous accédez à MSDN. Si le paramètre de l’utilisateur est local, tous les appels simplement accéder au moteur d’aide local.  
  
F1 diagramme de flux :  
  
![Flux F1](../../extensibility/internals/media/f1flow.png "F1flow")  
  
Lorsque la source de contenu d’aide par défaut la visionneuse d’aide a la valeur en ligne (lancement de navigateur) :  
  
-   Les fonctionnalités de Visual Studio partenaire (VSP) émettre une valeur pour le jeu de propriétés F1 (prefix.keyword sac de propriétés et des URL en ligne pour le préfixe trouvé dans le Registre) : F1 envoie une URL VSP + paramètres dans le navigateur.  
  
-   Fonctionnalités de Visual Studio (éditeur de langage, les éléments de menu spécifiques de Visual Studio, etc.) : F1 envoie une URL de Visual Studio dans le navigateur.  
  
Lorsque la source de contenu d’aide par défaut la visionneuse d’aide est définie à l’aide locale (lancement dans la visionneuse d’aide) :  
  
-   Fonctionnalités VSP où le mot clé correspondent entre sac F1 et des index de magasin local (autrement dit, le prefix.keyword sac de propriété = valeur trouvée dans l’index du magasin local) : F1 affiche la rubrique dans la visionneuse d’aide.  
  
-   Fonctionnalités de Visual Studio (aucune option pour le fichier VSP remplacer le jeu de propriétés émis à partir des fonctionnalités de Visual Studio) : F1 restitue une rubrique dans la visionneuse d’aide Visual Studio.  
  
Définissez les valeurs de Registre suivantes pour activer (F1) de secours pour le contenu d’aide de fournisseur. F1 secours signifie que la visionneuse d’aide est définie à l’aide F1 rechercher en ligne, et que le contenu du fournisseur est installé localement pour le disque dur. La visionneuse d’aide doit ressembler à l’aide locale pour le contenu, même si le paramètre par défaut est de l’aide en ligne.  
  
1.  Définir le **VendorContent** valeur sous la clé de Registre 2.3 d’aide :  
  
    -   Pour les systèmes d’exploitation 32 bits :  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         « VendorContent » = DWORD : 00000001  
  
    -   Pour les systèmes d’exploitation 64 bits :  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         « VendorContent » = DWORD : 00000001  
  
2.  Enregistrer l’espace de noms de serveur partenaire sous la clé de Registre 2.3 d’aide :  
  
    -   Pour les systèmes d’exploitation 32 bits :  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< espace de noms\>*  
  
         « emplacement » = « hors connexion »  
  
    -   Pour les systèmes d’exploitation 64 bits :  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< espace de noms\>*  
  
         « emplacement » = « hors connexion »  
  
**Namespace natif l’analyse de base**  
  
Pour activer l’analyse de base native espace de noms, dans le Registre ajouter une nouvelle valeur de DWORD par le nom de : BaseNativeNamespaces et définissez sa valeur sur 1 (sous la clé de catalogue qu’ils souhaitent pour prendre en charge).  Par exemple, si vous souhaitez utiliser le catalogue de Visual Studio, vous pouvez ajouter la clé pour le chemin d’accès :  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
Lorsqu’un mot clé F1 dans le format de QU'EN-TÊTE/méthode est rencontrée, le caractère '/' sera analysé, ce qui entraîne la construction suivante :  
  
-   EN-tête : sera l’espace de noms peut être utilisé pour enregistrer dans le Registre  
  
-   MÉTHODE : cela devient le mot clé qui est passé par le biais.  
  
Par exemple, prenons une bibliothèque personnalisée appelée CustomLibrary et une méthode appelée MyTestMethod, lorsqu’une demande arrive il de F1 seront au format `CustomLibrary/MyTestMethod`.  
  
Un utilisateur peut inscrire CustomLibrary en tant que l’espace de noms sous la ruche de partenaires, puis fournir toute clé emplacement qu’il souhaite, et le mot clé transmis à la requête sera MyTestMethod.  
  
**Activer l’aide de l’outil dans l’IDE de débogage**  
  
Ajoutez la clé de Registre suivante et une valeur :  
  
Clé d’aide HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic : afficher la sortie de débogage dans la valeur de la vente au détail : Oui  
  
Dans l’IDE, dans le menu Aide, sélectionnez « Contexte d’aider à déboguer »  
  
**Métadonnées de contenu**  
  
Dans le tableau suivant, une chaîne qui s’affiche entre crochets est un espace réservé qui doit être remplacé par une valeur reconnue. Par exemple, dans \<meta name="Microsoft.Help.Locale » contenu = « [code de langue] » / >, « [code de langue] » doit être remplacé par une valeur comme « en-us ».  
  
|Propriété (représentation HTML)|Description|  
|--------------------------------------|-----------------|  
|\< contenu de métadonnées name="Microsoft.Help.Locale » = « [code de langue] » / >|Définit les paramètres régionaux de cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois et il doit être insérée au-dessus de toutes les autres balises de Microsoft Help. Si cette balise n’est pas utilisée, le corps du texte de la rubrique est indexé à l’aide des analyseurs lexicaux qui sont associé aux paramètres régionaux du produit, s’il est spécifié ; dans le cas contraire, l’en-us lexical est utilisé. Cette balise est conforme à la norme RFC 4646 ISOC. Pour vous assurer que Microsoft Help fonctionne correctement, utilisez cette propriété au lieu de l’attribut de langue général.|  
|\< contenu de métadonnées name="Microsoft.Help.TopicLocale » = « [code de langue] » / >|Définit les paramètres régionaux de cette rubrique lorsque d’autres paramètres régionaux est également utilisés. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Utilisez cette balise lorsque le catalogue contient le contenu de plusieurs langues. Plusieurs rubriques dans un catalogue peuvent avoir le même ID, mais chacun doit spécifier un TopicLocale unique. La rubrique qui spécifie un TopicLocale qui correspond aux paramètres régionaux du catalogue est le la rubrique qui s’affiche dans la table des matières. Toutefois, toutes les versions linguistiques de la rubrique sont affichées dans les résultats de la recherche.|  
|\< titre > [titre] \< /title >|Spécifie le titre de cette rubrique. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. Si le corps de la rubrique ne contient pas un titre \<div > section ce titre s’affiche dans la rubrique et dans la table des matières.|  
|\< nom de métadonnées = « Microsoft.Help.Keywords » contenu = « [aKeywordPhrase] » / >|Spécifie le texte d’un lien qui s’affiche dans le volet de l’index de la visionneuse d’aide. Un clic sur le lien, la rubrique s’affiche. Vous pouvez spécifier plusieurs mots clés d’index pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que des liens vers cette rubrique s’affichent dans l’index. Mots clés de « K » à partir de versions antérieures de l’aide peuvent être convertis en cette propriété.|  
|\< contenu de métadonnées name="Microsoft.Help.Id » = « [TopicID] » / >|Définit l’identificateur de cette rubrique. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. L’ID doit être unique parmi les rubriques dans le catalogue qui ont les mêmes paramètres régionaux. Dans une autre rubrique, vous pouvez créer un lien vers cette rubrique à l’aide de ce code.|  
|\< métadonnées name="Microsoft.Help.F1 « content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Spécifie le mot clé F1 de cette rubrique. Vous pouvez spécifier plusieurs mots-clés F1 pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que cette rubrique à afficher lorsque l’utilisateur d’une application appuie sur F1. En règle générale, seule de mot clé F1 est spécifié pour une rubrique. Mots clés de « F » à partir de versions antérieures de l’aide peuvent être convertis en cette propriété.|  
|\< nom de métadonnées = « Description » content = « [rubrique description] » / >|Fournit un bref résumé du contenu de cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Cette propriété est accessible directement par la bibliothèque de la requête ; Il n’est pas stocké dans le fichier d’index.|  
 contenu de métadonnées name="Microsoft.Help.TocParent » = « [parent_Id] » / >|Spécifie la rubrique parente de cette rubrique dans la table des matières. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. La valeur est le Microsoft.Help.Id du parent. Une rubrique peut avoir qu’un seul emplacement dans la table du contenu. « -1 » est considéré comme l’ID de rubrique pour la racine de la table des matières. Dans [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], que la page est la page d’accueil de la visionneuse d’aide. Il s’agit de la même raison, que nous ajoutons spécifiquement TocParent =-1 vers certaines rubriques pour vous assurer qu’ils apparaissent en haut niveau. La page d’accueil de la visionneuse d’aide est une page du système et donc non remplaçables. Si un VSP tente d’ajouter une page avec un ID de -1, il peut obtenir ajouté à l’ensemble de contenu, mais la visionneuse d’aide sera toujours utiliser la page system - accueil de visionneuse de l’aide|  
|\< contenu de métadonnées name="Microsoft.Help.TocOrder » = « [entier] » / >|Spécifie l’emplacement dans la table des matières de cette rubrique par rapport à ses sujets d’homologues. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. La valeur est un entier. Une rubrique qui spécifie un entier inférieur-valeur s’affiche au-dessus d’une rubrique qui spécifie un entier de la valeur plus élevée.|  
|\< contenu de métadonnées name="Microsoft.Help.Product » = « [product code] » / >|Spécifie le produit par cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Ces informations peuvent également être fournies en tant que paramètre passé à l’indexeur de l’aide.|  
|\< contenu de métadonnées name="Microsoft.Help.ProductVersion » = « [numéro de version] » / >|Spécifie la version du produit par cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Ces informations peuvent également être fournies en tant que paramètre passé à l’indexeur de l’aide.|  
|\< contenu de métadonnées name="Microsoft.Help.Category » = « [chaîne] » / >|Utilisé par les produits pour identifier les sous-sections de contenu. Vous pouvez identifier plusieurs sous-sections pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que des liens pour identifier les sous-sections. Cette balise est utilisée pour stocker les attributs pour TargetOS et TargetFrameworkMoniker lorsqu’une rubrique est convertie à partir d’une version antérieure de l’aide. Le format du contenu est AttributeName:AttributeValue.|  
|\< contenu de name="Microsoft.Help.TopicVersion Meta = « [numéro de version rubrique] » / >|Spécifie cette version de la rubrique lorsque plusieurs versions existent dans un catalogue. Microsoft.Help.Id n’est pas garanti pour être unique, cette balise est requise lorsque plusieurs versions d’une rubrique existent dans un catalogue, par exemple, lorsqu’un catalogue contient une rubrique pour le .NET Framework 3.5 et une rubrique pour le .NET Framework 4 et les deux ont le même Micro réversible. Help.Id.|  
|\< nom de métadonnées = le contenu de « SelfBranded » = « [TRUE ou FALSE] » / >|Spécifie si cette rubrique utilise le package de marque de démarrage du Gestionnaire de bibliothèque d’aide ou d’un package de personnalisation est spécifique à la rubrique. Cette balise doit être TRUE ou FALSE. Si la valeur est TRUE, le package de personnalisation pour la rubrique associée remplace le package de personnalisation qui est défini au Gestionnaire de bibliothèque d’aide afin que la rubrique est rendue comme prévu même si elle diffère le rendu d’un autre contenu. Si la valeur est FALSE, la rubrique active est rendue selon le package de personnalisation qui est défini au démarrage du Gestionnaire de bibliothèque d’aide. Par défaut, le Gestionnaire de bibliothèque d’aide suppose marque automatique pour avoir la valeur false, sauf si la variable SelfBranded est déclarée en tant que la valeur est TRUE ; Par conséquent, vous n’avez pas à déclarer \<nom meta = « SelfBranded » content = « FALSE » / >.|  
  
### <a name="creating-a-branding-package"></a>Création d’un package de marque  
La version de Visual Studio comprend un nombre des différents produits Visual Studio, y compris l’isolée et les interpréteurs de commandes intégrés pour Visual Studio partenaires.  Chacun de ces produits nécessite une certaine mesure basée sur une rubrique de contenu d’aide prise en charge, unique pour le produit de personnalisation.  Par exemple, les rubriques de Visual Studio faut une présentation de la marque cohérente, tandis que SQL Studio, qui encapsule l’interpréteur de commandes ISO, nécessite son propre contenu unique aide marque pour chaque rubrique.  Un partenaire de Shell intégré souhaitant les rubriques d’aide pour être dans le contenu d’aide Visual Studio produit parent tout en conservant leurs propres personnalisation de la rubrique.  
  
Personnalisation des packages sont installés par le produit contenant la visionneuse d’aide.  Pour les produits Visual Studio :  
  
-   Un package de marque de secours (Branding_\<paramètres régionaux > .mshc) est installé dans la racine d’application aide les 2.3 visionneuse (exemple : C:\Program Files (x86) \Microsoft Help Viewer\v2.3) par le module linguistique de la visionneuse d’aide.  Il est utilisé pour les cas où le produit marque le package n’est pas installé (aucun contenu n’a été installé) ou dans lequel le package de marque installé est endommagé.  Notez que les éléments de Visual Studio (logo et des commentaires) sont ignorés lorsque le secours de racine d’application marque le package est utilisé.  
  
-   Lorsque le contenu de Visual Studio est installé à partir du service de package de contenu, un package de personnalisation est également installé (pour le premier scénario d’installation du contenu de temps).  S’il existe une mise à jour pour le package de personnalisation, la mise à jour est installé lors de la prochaine mise à jour de contenu ou l’action d’installation de package supplémentaire se produit.  
  
La visionneuse d’aide Microsoft prend en charge la personnalisation des rubriques basées sur des métadonnées de la rubrique.  
  
-   Où les métadonnées de la rubrique définissent self marque = true, la rubrique est de rendu, ne rien faire (autant que la marque).  
  
-   Où les métadonnées de la rubrique définissent self marque = false, utilisez le package de personnalisation associé avec la valeur de métadonnées TopicVendor.  
  
-   Le contenu où les métadonnées de la rubrique définissent name="Microsoft.Help.TopicVendor » =\< marque nom du package dans le fournisseur MSHA >, utilisez le package de personnalisation défini dans la valeur de contenu.  
  
-   Notez que dans le catalogue de Visual Studio, il existe une application de la priorité des Packages de personnalisation.  Personnalisation de première Visual Studio par défaut est appliquée et puis, si définis dans les métadonnées de la rubrique et la prise en charge avec la personnalisation associés du package (comme défini dans l’installation msha), le fournisseur défini par la marque est appliqué comme un remplacement.  
  
Éléments de personnalisation se répartissent généralement en trois catégories principales :  
  
-   Éléments d’en-tête (exemples lien commentaires, texte d’exclusion conditionnelle, logo)  
  
-   Contenu des comportements (exemples incluent les éléments de texte du contrôle Développer/réduire et éléments de l’extrait de code)  
  
-   Éléments de pied de page (par exemple, Copyright)  
  
Éléments considérés comme des éléments personnalisés incluent (détaillée dans cette spécification) :  
  
-   Logo du catalogue/produit (par exemple, Visual Studio)  
  
-   Éléments de liaison et le courrier électronique des commentaires  
  
-   Texte d’exclusion  
  
-   Texte de copyright  
  
Fichiers de prise en charge dans le package de marque de visionneuse d’aide Visual Studio incluent :  
  
-   Graphiques (logos, icônes, etc.).  
  
-   Branding.js - prise en charge des comportements contenus des fichiers de script  
  
-   Branding.XML - chaînes utilisé de manière cohérente sur le contenu du catalogue.  Remarque : pour inclure des éléments de texte de localisation de Visual Studio dans le branding.xml, _locID = «\<valeur unique > »  
  
-   Branding.CSS - les définitions de style pour la cohérence de présentation  
  
-   Printing.CSS - présentation imprimée cohérente des définitions de style  
  
Comme indiqué ci-dessus, la personnalisation des Packages associés à la rubrique :  
  
-   Lorsque SelfBranded = false est définie dans les métadonnées, le catalogue de package de marque hérite de la rubrique  
  
-   Ou lorsque SelfBranded = false et il est un Package de marque unique défini dans le MSHA et disponible lorsque l’installation du contenu  
  
Pour vsp implémentation de packages marque personnalisées (contenu VSP, SelfBranded = True), une façon de procéder consiste à commencer par le package de marque secours (installé avec la visionneuse d’aide) et modifier le nom du fichier selon le cas.  Le Branding_\<paramètres régionaux > .mshc fichier est un fichier zip avec l’extension de fichier passé à .mshc, il vous suffit de modifier l’extension de .mshc par .zip et extraire le contenu.  Voir ci-dessous pour la personnalisation des éléments de package et de modifier si nécessaire (par exemple, modifier le logo et le logo VSP la référence au logo dans le fichier Branding.xml, mettre à jour Branding.xml par caractéristiques VSP, etc.).  
  
Lorsque toutes les modifications sont effectuées, créez un fichier zip contenant des éléments de personnalisation souhaités et remplacez l’extension .mshc.  
  
Pour associer le package de marque personnalisé, créez la MSHA qui contient la référence au fichier mshc marque en même temps que le contenu mshc (qui contient les rubriques).  Voir ci-dessous « MSHA » pour la création d’une base MSHA.  
  
Le fichier Branding.xml contient une utilisée pour le rendu de manière cohérente des éléments spécifiques dans une rubrique lors de la rubrique contient des éléments de liste \<meta name="Microsoft.Help.SelfBranded « contenu = « false » / >.  Vous trouverez ci-dessous la liste d’éléments dans le fichier Branding.xml Visual Studio.  Notez que cette liste est destinée à être utilisée en tant que modèle pour les personnes influentes ISO Shell, où ils modifient ces éléments (par exemple logo, commentaires et le Copyright) pour répondre à leur besoins de personnalisation du produit.  
  
Remarque : les variables relevées par « {n} » ont des dépendances de code - suppression ou modification de ces valeurs entraîne des erreurs et éventuellement le blocage d’application. Identificateurs de localisation (exemple _locID="codesnippet.n ») sont inclus dans le Package de personnalisation de Visual Studio.  
  
**Branding.Xml**  
  
|||  
|-|-|  
|Fonctionnalités :|**CollapsibleArea**|  
|Utiliser :|Développez le texte du contrôle de contenu est réduite|  
|**Élément**|**Valeur**|  
|ExpandText|Expand|  
|CollapseText|Réduire|  
|Fonctionnalités :|**CodeSnippet**|  
|Utiliser :|Texte de contrôle l’extrait de code.  Remarque : Contenu extrait de Code avec un espace « Sans rupture » est remplacé par espace.|  
|**Élément**|**Valeur**|  
|CopyToClipboard|Copier dans le Presse-papiers|  
|ViewColorizedText|Vue coloré|  
|CombinedVBTabDisplayLanguage|Visual Basic (exemple)|  
|VBDeclaration|Déclaration|  
|VBUsage|Utilisation|  
|Fonctionnalités :|**Logo des commentaires et un pied de page**|  
|Utiliser :|Fournir un contrôle de commentaires au client de fournir des commentaires sur la rubrique Active par courrier électronique.  Texte de copyright pour le contenu.  Définition de logo.|  
|**Élément**|**Valeur (ces chaînes peuvent être modifiées pour répondre aux besoins de contenu utilisateur précoce.)**|  
|Droits d’auteur|© 2013 Microsoft Corporation. Tous droits réservés.|  
|SendFeedback|\<un href = « {0} » {{1} > envoyer des commentaires\</a > sur cette rubrique à Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|Fonctionnalités :|**exclusion de responsabilité**|  
|Utiliser :|Le contenu traduit un ensemble de cas exclusions spécifiques pour l’ordinateur.|  
|**Élément**|**Valeur**|  
|MT_Editable|Cet article a été traduit. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne », pour afficher cette page en mode modifiable avec le contenu original en anglais, en même temps.|  
|MT_NonEditable|Cet article a été traduit. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne », pour afficher cette page en mode modifiable avec le contenu original en anglais, en même temps.|  
|MT_QualityEditable|Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne », pour afficher cette page en mode modifiable avec le contenu original en anglais, en même temps.|  
|MT_QualityNonEditable|Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne », pour afficher cette page en mode modifiable avec le contenu original en anglais, en même temps.|  
|MT_BetaContents|Cet article a été traduit automatiquement pour une version préliminaire. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne », pour afficher cette page en mode modifiable avec le contenu original en anglais, en même temps.|  
|MT_BetaRecycledContents|Cet article a été traduit manuellement pour la version préliminaire. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne », pour afficher cette page en mode modifiable avec le contenu original en anglais, en même temps.|  
|Fonctionnalités :|**Élément LinkTable**|  
|Utiliser :|Prise en charge des liens vers des rubriques en ligne|  
|**Élément**|**Valeur**|  
|LinkTableTitle|Table de liens|  
|TopicEnuLinkText|Afficher la version anglaise\</a > de cette rubrique est disponible sur votre ordinateur.|  
|TopicOnlineLinkText|Afficher cette rubrique \<un href = « {0} » {{1} > en ligne\</a >|  
|OnlineText|Online|  
|Fonctionnalités :|**Contrôle Audio vidéo**|  
|Utiliser :|Afficher les éléments et du texte pour le contenu vidéo|  
|**Élément**|**Valeur**|  
|MultiMediaNotSupported|Internet Explorer 9 ou supérieure doit être installé pour prendre en charge le contenu de {0}.|  
|VideoText|afficher la vidéo|  
|Audiotexte|flux de données audio|  
|OnlineVideoLinkText|\<p > pour afficher la vidéo de cette rubrique, cliquez sur {0}\<un href = « \ {1\\} » > {2}here\</a >.\< /p >|  
|OnlineAudioLinkText|\<p > pour écouter le fichier audio associé à cette rubrique, cliquez sur {0}\<un href = « \ {1\\} » > {2}here\</a >.\< /p >|  
|Fonctionnalités :|**Contrôle de contenu de pas installé**|  
|Utiliser :|Éléments de texte (chaînes) utilisés pour le rendu de contentnotinstalled.htm|  
|**Élément**|**Valeur**|  
|ContentNotInstalledTitle|Aucun contenu n’a été trouvé sur votre ordinateur.|  
|ContentNotInstalledDownloadContentText|\<p > pour télécharger le contenu sur votre ordinateur, \<un href = « {0} » {{1} > cliquez sur l’onglet gérer\</a >.\< /p >|  
|ContentNotInstalledText|\<p > aucun contenu n’est installé sur votre ordinateur. Contactez votre administrateur pour l’installation du contenu d’aide locale. \</p >|  
|Fonctionnalités :|**Contrôle de rubrique introuvable**|  
|Utiliser :|Éléments de texte (chaînes) utilisés pour le rendu de topicnotfound.htm|  
|**Élément**|**Valeur**|  
|TopicNotFoundTitle|Impossible de trouver la rubrique demandée sur votre ordinateur.|  
|TopicNotFoundViewOnlineText|\<p > la rubrique que vous avez demandée est introuvable sur votre ordinateur, mais vous pouvez \<un href = « {0} » {{1} > Afficher la rubrique en ligne\</a >.\< /p >|  
|TopicNotFoundDownloadContentText|\<p > consultez le volet de navigation pour obtenir des liens vers des rubriques similaires ou \<un href = « {0} » {{1} > cliquez sur l’onglet gérer\</a > pour télécharger le contenu sur votre ordinateur.\< /p >|  
|TopicNotFoundText|\<p > la rubrique que vous avez demandée est introuvable sur votre ordinateur. \</p >|  
|Fonctionnalités :|**Rubrique endommagé contrôle**|  
|Utiliser :|Éléments de texte (chaînes) utilisés pour le rendu de topiccorrupted.htm|  
|**Élément**|**Valeur**|  
|TopicCorruptedTitle|Impossible d’afficher la rubrique demandée.|  
|TopicCorruptedViewOnlineText|\<p > la visionneuse d’aide ne peut pas afficher la rubrique demandée. Il peut y avoir une erreur dans le contenu de la rubrique ou une dépendance de système sous-jacent. \</p >|  
|Fonctionnalités :|**Contrôle de la Page d’accueil**|  
|Utiliser :|Texte prenant en charge l’affichage du contenu du nœud de niveau supérieur de la visionneuse d’aide.|  
|**Élément**|**Valeur**|  
|HomePageTitle|Accueil de visionneuse d’aide|  
|HomePageIntroduction|\<p > Bienvenue dans la visionneuse d’aide Microsoft, une source essentielle des informations relatives à toute personne qui utilise les outils, produits, technologies et services Microsoft. La visionneuse d’aide vous donne accès aux informations de référence et de procédure, exemple de code, des articles techniques et bien plus encore. Pour rechercher le contenu que vous avez besoin, parcourez la table des matières, utilisez la recherche en texte intégral ou parcourez le contenu à l’aide de l’index de mots clés. \</p >|  
|HomePageContentInstallText|\<p >\<br / > utiliser le \<un href = « {0} » {{1} > Gérer le contenu\</a > onglet pour effectuer les opérations suivantes :\<ul >\<li > ajouter du contenu sur votre ordinateur.\< /li >\<li > Vérifiez les mises à jour à votre contenu local.\< /li >\<li > Supprimer le contenu de votre ordinateur.\< /li >\</ul >\</p >|  
|HomePageInstalledBooks|Documentation installée|  
|HomePageNoBooksInstalled|Aucun contenu n’a été trouvé sur votre ordinateur.|  
|HomePageHelpSettings|Paramètres de contenu d’aide|  
|HomePageHelpSettingsText|\<p > votre réglage actuel est l’aide locale. La visionneuse d’aide affiche le contenu que vous avez installée sur votre ordinateur. \<br / > pour modifier la source de contenu de l’aide sur la barre de menus de Visual Studio, choisissez \<span style = « {0} » > aide, définir les préférences aide\</span >.\< br / >\</p >|  
|Mégaoctet (Mo)|MO|  
  
**branding.js**  
  
Le fichier branding.js contient JavaScript utilisé par les éléments de personnalisation de visionneuse d’aide Visual Studio.  Voici une liste des éléments de personnalisation de la fonction JavaScript prise en charge.  Toutes les chaînes à localiser ce fichier sont définies dans la section « Chaînes localisables » en haut de ce fichier.  Notez que les fichiers ICL a été créé pour les chaînes d’emplacement dans le fichier branding.js.  
  
||||  
|-|-|-|  
|**Fonctionnalité de personnalisation**|**Fonction JavaScript**|**Description**|  
|Var...||Définir des variables|  
|Obtenir le langage de code utilisateur|setUserPreferenceLang|mappe un index de # pour le langage de code|  
|Définir et obtenir des valeurs de cookie|getCookie, setCookie||  
|Membre hérité|changeMembersLabel|Développer/réduire le membre hérité|  
|Lorsque SelfBranded = False|onLoad|Lire la chaîne de requête pour vérifier s’il est une demande d’impression.  Définir tous les codesnippets concentrer l’onglet par défaut d’utilisateur.  S’il s’agit d’une impression demande puis définissez isPrinterFriendly sur true. Vérifier le mode de contraste élevé.|  
|Extrait de code|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Onglet||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|écrire tous les objets contrôle réductible dans la liste.|  
||CA_Click|en fonction de l’état de la zone réductible, qui définit les images et le texte pour présenter|  
|Prise en charge du contraste de Logo|isBlackBackground()|Appelé pour déterminer si l’arrière-plan est noir.  Précise uniquement lorsque le mode de contraste élevé.|  
||isHighContrast()|Utilisez un intervalle de couleur pour détecter le mode de contraste élevé|  
||onHighContrast(black)|Appelé lors de la détection de contraste élevé|  
|Fonctionnalités LST|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|Fonctionnalités multimédias|légende (début, fin, de texte, de style)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (styleName, styleValue)||  
||showCC(id)||  
||Subtitle(ID)||  
  
**FICHIERS HTM**  
  
Le package de personnalisation contient un ensemble de fichiers HTM qui prennent en charge les scénarios de communication des informations de clé pour les utilisateurs de contenu d’aide, par exemple une page d’accueil qui contient une section qui décrit les ensembles de contenus sont installés et les pages qui informe l’utilisateur lorsque les rubriques ne peut pas est introuvable dans le jeu local de rubriques. Notez que ces fichiers HTM peuvent être modifiées par produit.  Fournisseurs d’interpréteur de commandes ISO sont en mesure de prendre le package de marque par défaut et modifier le comportement et le contenu de ces pages à la suite de leurs besoins.  Ces fichiers font référence à leur package respectif de personnalisation dans l’ordre pour les balises de personnalisation obtenir le contenu correspondant à partir du fichier branding.xml.  
  
||||  
|-|-|-|  
|**Fichier**|**Utilisez**|**Affiche la Source de contenu**|  
|homepage.htm|Il s’agit d’une page qui affiche le contenu actuellement installé et tout autre message approprié pour présenter à l’utilisateur sur leur contenu.  Ce fichier contient le contenu « Microsoft.Help.Id » de l’attribut de données supplémentaire meta = « -1 » qui place ce contenu en haut de la table des matières de contenu local.||  
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.XML, balise \<HomePageTitle >|  
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.XML, balise \<HomePageIntroduction >|  
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.XML, balise \<HomePageContentInstallText >|  
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Titre de section Branding.xml balise\<HomePageInstalledBooks >, les données générées à partir de l’application, \<HomePageNoBooksInstalled > lorsque aucune documentation n’est installée.|  
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Titre de section Branding.xml balise \<HomePageHelpSettings >, section texte \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Lorsqu’une rubrique existe déjà dans le jeu local, mais pour une raison quelconque ne peut pas être affichée (endommagé contenu).||  
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, balise \<TopicCorruptedTitle >|  
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.XML, balise \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Lorsqu’une rubrique est introuvable dans le contenu local défini ni disponible en ligne||  
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.XML, balise \<TopicNotFoundTitle >|  
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.XML, balise \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, balise \<TopicNotFoundText >|  
|contentnotinstalled.htm|Lorsqu’il n’existe pas de contenu local installé pour le produit.||  
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.XML, balise \<ContentNotInstalledTitle >|  
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.XML, balise \<ContentNotInstalledDownloadContentText >|  
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.XML, balise \<ContentNotInstalledText >|  
  
**Fichiers CSS**  
  
Le Package Visual Studio aide visionneuse marque contient deux fichiers css pour prendre en charge la présentation du contenu cohérente aide de Visual Studio :  
  
-   Branding.CSS - contient les éléments css pour le rendu where SelfBranded = false  
  
-   Printer.CSS - contient les éléments css pour le rendu where SelfBranded = false  
  
Branding.CSS fichiers inclut des définitions pour la présentation de rubrique Visual Studio (inconvénient est que le branding.css contenue dans le Branding_\<paramètres régionaux > .mshc à partir du service de package peut varier).  
  
**Fichiers graphiques**  
  
Le contenu Visual Studio affiche un logo de Visual Studio, ainsi que des autres graphiques.  Vous trouverez ci-dessous la liste complète des fichiers graphiques dans le package de marque de visionneuse d’aide Visual Studio.  
  
||||  
|-|-|-|  
|**Fichier**|**Utilisez**|**Exemples**|  
|Clear.gif|Utilisé pour afficher une zone réductible||  
|footer_slice.gif|Présentation de pied de page||  
|info_icon.gif|Utilisé lors de l’affichage des informations|Exclusion de responsabilité|  
|online_icon.gif|Cette icône doit être associé à liens en ligne||  
|tabLeftBD.gif|Utilisé pour afficher le conteneur d’extrait de code||  
|tabRightBD.gif|Utilisé pour afficher le conteneur d’extrait de code||  
|vs_logo_bk.gif|Utilisé pour les références de logo de contraste normal, tel que défini dans la balise de Branding.xml \<LogoFileName >.  Pour les produits Visual Studio, le nom du logo est vs_logo_bk.gif.||  
|vs_logo_wh.gif|Utilisé pour les références de logo haute normal, tel que défini dans la balise de Branding.xml \<LogoFileNameHC >.  Pour les produits Visual Studio, le nom du logo est vs_logo_wh.gif.||  
|ccOff.png|Graphique de sous-titrage||  
|ccOn.png|Graphique de sous-titrage||  
|ImageSprite.png|Utilisé pour afficher une zone réductible|développer ou réduire le graphique|  
  
### <a name="deploying-a-set-of-topics"></a>Déploiement d’un ensemble de rubriques  
Il s’agit d’un didacticiel très simple et rapide pour la création d’un déploiement de contenu de la visionneuse d’aide définir composé d’un fichier MSHA et de l’ensemble de fichiers CAB ou MSHC qui contient les rubriques. Le MSHA est un fichier XML qui décrit un ensemble de fichiers CAB ou les fichiers MSHC. La visionneuse d’aide peut lire le MSHA pour obtenir une liste de contenu (le fichier. Fichier CAB ou. Les fichiers MSHC) disponibles pour l’installation locale.  
  
Il s’agit uniquement une introduction décrivant le schéma XML très basique pour le MSHA Observateur d’aide.  Notez qu’il existe un exemple d’implémentation sous cette vue d’ensemble et exemples helpcontentsetup.msha.  
  
Le nom de la MSHA, dans le cadre de ce manuel, est helpcontentsetup.msha (le nom du fichier peut être n’importe quoi, avec l’extension. MSHA). Helpcontentsetup.msha (exemple ci-dessous) doit contenir une liste des fichiers CAB MSHCs disponibles.  Notez que le type de fichier doit être cohérent avec la MSHA (ne prend pas en charge une combinaison de types de fichiers MSHA et le fichier CAB). Pour chaque fichier CAB ou MSHC, il doit être un \<div classe = « package » >... \</div > (voir l’exemple ci-dessous).  
  
Remarque : dans l’exemple d’implémentation ci-dessous, nous avons inclus le package de personnalisation. Il est essentiel d’inclure afin d’obtenir les éléments de rendu du contenu de Visual Studio nécessaires et les comportements de contenu.  
  
Exemple de fichier helpcontentsetup.msha : (remplacez « contenu set nom 1 » et « contenu jeu nom 2 » etc. avec vos noms de fichiers.)  
  
```html
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>.  
  
```  
  
1.  Créez un dossier local, quelque chose comme « C:\SampleContent »  
  
2.  Pour cet exemple, nous allons utiliser les fichiers MSHC pour contenir les rubriques.  Un MSHC est un fichier zip avec l’extension de fichier a été remplacée par .zip pour. MSHC.  
  
3.  Créer le ci-dessous helpcontentsetup.msha comme un fichier texte (le bloc-notes a été utilisé pour créer le fichier) et enregistrez-le dans le dossier indiqué ci-dessus (voir l’étape 1).  
  
Notez que la classe « Personnalisation » existe et qu’il est unique. La personnalisation mshc est inclus dans cette introduction afin que le contenu installé sera marque, et les comportements de contenu qui sont contenus dans les MSHCs aura les éléments de support technique appropriée contenues dans le package de personnalisation. Sans cela, les erreurs entraîne lorsque le système recherche les éléments de prise en charge qui ne font pas partie des extraits (installé) contenu.  
  
Pour obtenir Visual Studio package de marque, copiez le fichier Branding_en-US.mshc sur C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ dans votre dossier de travail.  
  
```html  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>  
<div class="package">  
<span class="packageType">branding</span>  
<span class="name">Branding_en-US</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Résumé**  
  
Utilisation et extension les étapes ci-dessus activera vsp déployer leurs jeux de contenu de la visionneuse d’aide Visual Studio.  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Ajout de l’aide de Visual Studio Shell (intégré et isolé)  
**Introduction**  
  
Cette procédure pas à pas montre comment incorporer le contenu d’aide dans une application de Shell Visual Studio, puis le déployer.  
  
**Spécifications**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 isolé Redist du Shell](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**Vue d’ensemble**  
  
Le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] interpréteur de commandes est une version de la [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE sur laquelle vous pouvez baser une application. De telles applications contiennent le Shell isolé avec les extensions que vous créez. Utiliser des modèles de projet de Shell isolé, qui sont inclus dans le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, de générer des extensions.  
  
Les étapes de base pour la création d’une application de Shell isolé et son aide :  
  
1.  Obtenir le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistribuable (téléchargement Microsoft).  
  
2.  Dans Visual Studio, créez une extension d’aide qui est basée sur le Shell isolé, par exemple, l’extension de l’aide de Contoso qui est décrite plus loin dans cette procédure pas à pas.  
  
3.  Encapsuler l’extension et l’interpréteur de commandes ISO redistribuables dans un déploiement MSI (une installation de l’application). Cette procédure pas à pas n’inclut pas d’une étape d’installation.  
  
Créer un magasin de contenu Visual Studio. Pour le scénario de l’environnement intégré, modifiez la Visual Studio12 au nom de catalogue du produit, comme suit :  
  
-   Créez le dossier C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.  
  
-   Créez un fichier nommé que CatalogType.xml et l’ajouter au dossier. Le fichier doit contenir les lignes de code suivantes :  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
Définir le magasin de contenu dans le Registre. Pour l’environnement intégré, modifiez le nom du catalogue produit VisualStudio15 :  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     Clé : Valeur de chaîne de LocationPath : C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     Clé : Valeur de chaîne du nom de catalogue : [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation  
  
**Créer le projet**  
  
Pour créer une extension de Shell isolé :  
  
1.  Dans Visual Studio, sous **fichier**, choisissez **nouveau projet**, sous **autres Types de projets** choisissez **extensibilité**, puis choisissez  **Shell isolé Visual Studio**. Nommez le projet `ContosoHelpShell`) pour créer un projet d’extensibilité basé sur le modèle de Shell isolé Visual Studio.  
  
2.  Dans l’Explorateur de solutions, dans le projet ContosoHelpShellUI, dans le dossier de fichiers de ressources, ouvrez ApplicationCommands.vsct. Assurez-vous que cette ligne est commentée (recherchez « No_Help ») : `<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  Appuyez sur la touche F5 pour compiler et exécuter **déboguer**. Dans l’instance expérimentale de l’IDE de Shell isolé, choisissez le **aide** menu. Assurez-vous que le **afficher l’aide**, **ajouter et supprimer le contenu d’aide**, et **aider à définir les préférences** commandes apparaissent.  
  
4.  Dans l’Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier Shell Customization, ouvrez ContosoHelpShell.pkgdef. Pour définir le catalogue d’aide de Contoso, ajoutez les lignes suivantes :  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  Dans l’Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier Shell Customization, ouvrez ContosoHelpShell.Application.pkgdef. Pour activer la touche F1, ajoutez les lignes suivantes :  
  
    ```  
    // F1 Help Provider  
  
    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="13407"  
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"  
    @="Help3 Provider"  
    [$RootKey$\HelpProviders]  
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"  
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="Help3 Provider"  
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  Dans l’Explorateur de solutions, dans le menu contextuel de la solution ContosoHelpShell, choisissez le **propriétés** élément de menu. Sous **propriétés de Configuration**, sélectionnez **Configuration Manager**. Dans le **Configuration** colonne, modifiez toutes les valeurs « Debug » à « Libérer ».  
  
7.  Générez la solution. Cela crée un ensemble de fichiers dans un dossier de mise en production, qui sera utilisé dans la section suivante.  
  
Pour effectuer ce test comme si déployé :  
  
1.  Sur l’ordinateur que vous déployez Contoso pour installer l’interpréteur de commandes ISO (supérieure) téléchargé.  
  
2.  Créer un dossier dans \\\Program Files (x86)\\et nommez-le `Contoso`.  
  
3.  Copiez le contenu du dossier de mise en production ContosoHelpShell à \\dossier de \Contoso\ \Program Files (x86).  
  
4.  Démarrez l’Éditeur du Registre en choisissant **exécuter** dans les **Démarrer** menu et en entrant `Regedit`. Dans l’Éditeur du Registre, choisissez **fichier**, puis **importation**. Recherchez le dossier du projet ContosoHelpShell. Dans le sous-dossier ContosoHelpShell, choisissez ContosoHelpShell.reg.  
  
5.  Créer un magasin de contenu :  
  
     Pour l’interpréteur de commandes ISO - créer un magasin de contenu Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     Pour [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell intégré, créez le dossier C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  Créer que CatalogType.xml et ajouter au magasin de contenu (étape précédente) qui contient :  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Ajoutez les clés de Registre suivantes :  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key : Valeur de chaîne de LocationPath :  
  
     Pour ISO Shell :  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Environnement intégré :  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-des États-Unis  
  
     Clé : Valeur de chaîne du nom de catalogue : [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation. Pour ISO Shell, il s’agit de celui de votre catalogue.  
  
8.  Copier le contenu (fichiers CAB ou MSHC et MSHA) dans un dossier local.  
  
9. Ligne de commande exemple environnement intégré pour le test du magasin de contenu. Pour ISO Shell, modifiez les valeurs de catalogue et launchingApp comme il convient de faire correspondre le produit.  
  
     « C:\Program fichiers (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe » /catalogName VisualStudio15 /helpQuery méthode = « page & id = ContosoTopic0 » /launchingApp Microsoft, Visual Studio, 12.0  
  
10. Lancez l’application Contoso (à partir de la racine d’application Contoso). Dans l’interpréteur de commandes ISO, choisissez le **aide** élément de menu, puis remplacez le **aider à définir les préférences** à **utilisation de l’aide locale**.  
  
11. Dans l’interpréteur de commandes, choisissez le **aide** élément de menu, puis **afficher l’aide**. Doit se lancer la visionneuse d’aide locale. Choisissez l’onglet **Gérer le contenu**. Sous **Source d’Installation**, choisissez le **disque** case d’option. Choisissez le **...**  bouton et accédez au dossier local qui contient le contenu de Contoso (copié dans le dossier local dans l’étape ci-dessus). Choisissez le helpcontentsetup.msha. Contoso doit maintenant apparaître en tant qu’un livre dans les sélections de livre. Choisissez **ajouter**, puis choisissez le **mise à jour** bouton (en bas à droite).  
  
12. Dans l’IDE de Contoso, appuyez sur la touche F1 pour tester la fonctionnalité de la touche F1.  
  
### <a name="additional-resources"></a>Ressources supplémentaires  
L’API de Runtime, consultez [API de l’aide Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
Pour plus d’informations sur la façon de tirer parti de l’API de l’aide, consultez [aide des exemples de Code visionneuse](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
Pour fournir des commentaires sur ces composants, utilisez [Microsoft Connect](http://connect.microsoft.com/).  
  
Veuillez envoyer vos suggestions de fonctionnalité à [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
Pour obtenir une aide supplémentaire, essayez le [système d’aide et de Documentation pour développeurs MSDN forums](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
Mises à jour importantes du problème, consultez le [aide fichier Lisez-moi de visionneuse](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
Pour contacter l’équipe PM de visionneuse aide directement, envoyez un e-mail à hlpfdbk@microsoft.com