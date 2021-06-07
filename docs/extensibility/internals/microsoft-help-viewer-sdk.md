---
title: Kit de développement logiciel (SDK) Microsoft Help Viewer | Microsoft Docs
description: Découvrez les tâches de la visionneuse d’aide de Visual Studio, telles que la création d’un article, la création d’un package de personnalisation de la visionneuse d’aide et le déploiement d’un ensemble d’articles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bc2ed473e25dc75d0155bc864aa02c157e3482f
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448322"
---
# <a name="microsoft-help-viewer-sdk"></a>Kit SDK de Microsoft Help Viewer

Cet article contient les tâches suivantes pour les intégrateurs de la visionneuse d’aide de Visual Studio :

- Création d’une rubrique (prise en charge de F1)

- Création d’un package de personnalisation de contenu de la visionneuse d’aide

- Déploiement d’un ensemble d’Articles

- Ajout d’aide au shell Visual Studio (intégré ou isolé)

- Ressources supplémentaires

## <a name="create-a-topic-f1-support"></a>Créer une rubrique (prise en charge de F1)

Cette section fournit une vue d’ensemble des composants d’une rubrique présentée, des spécifications de rubrique, une brève description de la création d’une rubrique (y compris les exigences de prise en charge de F1) et enfin, une rubrique d’exemple avec son résultat rendu.

**Vue d’ensemble de la rubrique Help Viewer**

Quand une rubrique est appelée pour le rendu, la visionneuse d’aide obtient les éléments de package de personnalisation qui sont associés à la rubrique au moment de l’installation ou de la dernière mise à jour, ainsi que la rubrique XHTML, et combine les deux pour générer l’affichage de contenu présenté (données de personnalisation + données de rubrique).  Le package de personnalisation contient des logos, la prise en charge des comportements de contenu et le texte de personnalisation (Copyright, etc.).  Pour plus d’informations sur les éléments de package de personnalisation, consultez « Création d’un package de personnalisation » ci-dessous.  S’il n’existe aucun package de personnalisation associé à la rubrique, la visionneuse d’aide utilise le package de personnalisation de secours situé dans la racine de l’application de la visionneuse d’aide (Branding_en-US. MShC).

**Configuration requise pour la rubrique de la visionneuse d’aide**

Pour être rendu correctement dans la visionneuse d’aide, le contenu brut de la rubrique doit être le W3C Basic 1,1 XHTML.

Une rubrique contient généralement deux sections :

- Métadonnées (consultez informations de référence sur les métadonnées de contenu) : données sur la rubrique, par exemple, ID unique de la rubrique, valeur du mot clé, ID de la table des matières, ID du nœud parent, etc.

- Contenu du corps : conforme à la norme W3C Basic 1,1 XHTML, qui comprend des comportements de contenu pris en charge (zone réductible, extrait de code, etc.). Une liste complète est indiquée ci-dessous).

Contrôles pris en charge pour le package de personnalisation Visual Studio :

- Liens

- CodeSnippet

- CollapsibleArea

- Membre hérité

- LanguageSpecificText

Chaînes de langue prises en charge (ne respectant pas la casse) :

- javascript

- CSharp ou c #

- Cplusplus ou VisualC + + ou c++

- jscript

- VisualBasic ou VB

- f # ou FSharp ou FS

- autre-une chaîne qui représente un nom de langue

**Création d’une rubrique de la visionneuse d’aide**

Créez un nouveau document XHTML nommé ContosoTopic4.htm et incluez la balise title (ci-dessous).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Ensuite, ajoutez des données pour définir le mode de présentation de la rubrique (propre ou non), comment faire référence à cette rubrique pour la touche F1, où cette rubrique existe dans la table des matières, son ID (pour la référence de lien par d’autres rubriques), etc. Pour obtenir la liste complète des métadonnées prises en charge, consultez le tableau « métadonnées de contenu » ci-dessous.

- Dans ce cas, nous utiliserons notre propre package de personnalisation, une variante du package de personnalisation de la visionneuse de l’aide de Visual Studio.

- Ajoutez le nom méta et la valeur ("Microsoft. Help. F1" Content = "ContosoTopic4") qui correspondront à la valeur F1 fournie dans le conteneur de propriétés IDE. (Pour plus d’informations, consultez la section prise en charge de F1.) Il s’agit de la valeur qui est mise en correspondance avec l’appel F1 à partir de l’IDE pour afficher cette rubrique lorsque la touche F1 est sélectionnée dans l’IDE.

- Ajoutez l’ID de la rubrique. Il s’agit de la chaîne utilisée par d’autres rubriques pour créer un lien vers cette rubrique. Il s’agit de l’ID de la visionneuse d’aide pour cette rubrique.

- Pour la table des matières, ajoutez le nœud parent de cette rubrique pour définir l’emplacement où ce nœud de la table des matières doit apparaître.

- Pour la table des matières, ajoutez l’ordre des nœuds de cette rubrique. Lorsque le nœud parent possède un `n` nombre de nœuds enfants, définissez dans l’ordre des nœuds enfants l’emplacement de cette rubrique. Par exemple, cette rubrique est le numéro 4 de 4 rubriques enfants.

Exemple de section de métadonnées :

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

**Corps de la rubrique**

Le corps (à l’exclusion de l’en-tête et du pied de page) de la rubrique contient des liens de page, une section de note, une zone réductible, un extrait de code et une section de texte spécifique à une langue.  Pour plus d’informations sur les zones de la rubrique présentée, consultez la section relative à la personnalisation.

1. Ajoutez une balise de titre de rubrique :  `<div class="title">Contoso Topic 4</div>`

2. Ajoutez une section Note : `<div class="alert"> add your table tag and text </div>`

3. Ajouter une zone réductible :  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Ajoutez un extrait de code :  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Ajoutez du texte spécifique à une langue :  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Notez que `devLangnu=` vous pouvez entrer d’autres langues. Par exemple, `devLangnu="Fortran"` affiche Fortran lorsque l’extrait de code DisplayLanguage = Fortran

6. Ajouter des liens de page : `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Remarque : pour une nouvelle « langue d’affichage » non prise en charge (par exemple, F #, COBOL, Fortran), colorisation de code dans l’extrait de code est monochrome.

**Exemple de rubrique de la visionneuse d’aide** Le code illustre comment définir des métadonnées, un extrait de code, une zone réductible et du texte spécifique à une langue.

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
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**Prise en charge F1**

Dans Visual Studio, la sélection de F1 génère des valeurs fournies à partir de la position du curseur dans l’IDE et remplit un « jeu de propriétés » avec les valeurs fournies (en fonction de l’emplacement du curseur. Lorsque le curseur se trouve sur la fonctionnalité x, la fonctionnalité x est active/activée et remplit le jeu de propriétés avec des valeurs.  Lorsque la touche F1 est sélectionnée, le conteneur des propriétés est rempli et le code F1 Visual Studio vérifie si la source d’aide par défaut des clients est locale ou en ligne (Online est la valeur par défaut). crée ensuite la chaîne appropriée en fonction du paramètre Users (Online est l’interface par défaut)-Shell Execute (voir le Guide de l’administrateur de l’aide pour les paramètres de lancement exe) avec les paramètres de la visionneuse d’aide locale + le ou les mots clés du conteneur de propriétés si l’aide locale est la valeur par défaut , ou l’URL MSDN avec le mot clé dans la liste de paramètres.

Si trois chaînes sont retournées pour la touche F1, appelées « chaîne à valeurs multiples », prenez le premier terme, recherchez un accès et, le cas échéant, nous avons terminé ; Si ce n’est pas le cas, passez à la chaîne suivante.  Commandez des questions. La présentation des mots clés à valeurs multiples doit être une chaîne la plus longue à la chaîne la plus petite.  Pour vérifier cela dans le cas des mots clés à valeurs multiples, examinez la chaîne d’URL F1 en ligne, qui inclura le mot clé choisi.

Dans Visual Studio 2012, nous avons intentionnellement effectué une division plus forte entre Online et offline, de sorte que si le paramètre de l’utilisateur était pour Online, nous transmettons simplement la requête F1 directement à notre service de requête en ligne sur MSDN plutôt que de le Router via l’agent de bibliothèque d’aide que nous avions dans Visual Studio 2010. Nous recherchons ensuite un état « le contenu du fournisseur est installé = true » pour déterminer s’il faut effectuer une opération différente dans ce contexte. Si la valeur est true, nous effectuons ensuite cette logique d’analyse et de routage en fonction de ce que vous souhaitez prendre en charge pour vos clients. Si la valeur est false, nous allons simplement accéder à MSDN. Si le paramètre de l’utilisateur est local, tous les appels passent au moteur d’aide local.

Diagramme de Flow F1 :

![Flux F1](../../extensibility/internals/media/f1flow.png "F1flow")

Lorsque la source de contenu de l’aide par défaut de la visionneuse d’aide est définie sur en ligne (lancer dans le navigateur) :

- Les fonctionnalités de Visual Studio Partner (VSP) émettent une valeur dans le conteneur de propriétés F1 (préfixe du jeu de propriétés. mot clé et URL en ligne pour le préfixe trouvé dans le registre) : F1 envoie une URL et des paramètres VSP au navigateur.

- Fonctionnalités de Visual Studio (éditeur de langage, éléments de menu spécifiques à Visual Studio, etc.) : F1 envoie une URL Visual Studio au navigateur.

Quand la source de contenu de l’aide par défaut de la visionneuse d’aide est définie sur l’aide locale (lancer dans la visionneuse d’aide) :

- Les fonctionnalités VSP dont le mot clé correspond au jeu de propriétés F1 et à l’index de magasin local (autrement dit, le préfixe du jeu de propriétés. Keyword = la valeur trouvée dans l’index local du magasin) : F1 restitue la rubrique dans la visionneuse d’aide.

- Fonctionnalités de Visual Studio (aucune option pour que VSP ne remplace le conteneur de propriétés émis à partir des fonctionnalités de Visual Studio) : F1 affiche une rubrique Visual Studio dans la visionneuse d’aide.

Définissez les valeurs de Registre suivantes pour activer la touche F1 de secours pour le contenu de l’aide du fournisseur. La touche F1 de secours signifie que la visionneuse d’aide est configurée pour rechercher le contenu d’aide F1 en ligne et que le contenu du fournisseur est installé localement sur le disque dur de l’utilisateur. La visionneuse d’aide doit consulter l’aide locale du contenu, même si le paramètre par défaut est pour l’aide en ligne.

1. Définissez la valeur **VendorContent** sous la clé de registre help 2,3 :

   - Pour les systèmes d’exploitation 32 bits :

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword : 00000001

   - Pour les systèmes d’exploitation 64 bits :

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword : 00000001

2. Inscrivez l’espace de noms du partenaire sous la clé de Registre help 2,3 :

   - Pour les systèmes d’exploitation 32 bits :

      <em> \\ Espace de noms \> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<</em>

      "location" = "Offline"

   - Pour les systèmes d’exploitation 64 bits :

      <em> \\ Espace de noms \> HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<</em>

      "location" = "Offline"

**Analyse de base de l’espace de noms natif**

Pour activer l’analyse de l’espace de noms natif de base, dans le registre, ajoutez un nouveau DWORD par le nom de : BaseNativeNamespaces et définissez sa valeur sur 1 (sous la clé de catalogue qu’il souhaite prendre en charge).  Par exemple, si vous souhaitez utiliser le catalogue Visual Studio, vous pouvez ajouter la clé au chemin d’accès :

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Quand un mot clé F1 dans l’en-tête/la méthode de format est rencontré, le caractère « / » est analysé, ce qui entraîne la construction suivante :

- EN-tête : sera l’espace de noms qui peut être utilisé pour l’inscription dans le registre

- MÉTHODE : devient le mot clé qui est passé.

Par exemple, dans le cas d’une bibliothèque personnalisée appelée CustomLibrary et d’une méthode appelée MyTestMethod, quand une requête F1 arrive, elle est mise en forme en tant que `CustomLibrary/MyTestMethod` .

Un utilisateur peut ensuite inscrire CustomLibrary comme espace de noms sous la ruche partenaires, et indiquer la clé d’emplacement qu’il souhaite, et le mot clé transmis à la requête sera MyTestMethod.

**Activer l’outil de débogage de l’aide dans l’IDE**

Ajoutez la clé de Registre et la valeur suivantes :

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Valeur : afficher la sortie de débogage dans les données de vente au détail : Oui

Dans l’IDE, sous l’élément de menu aide, sélectionnez **déboguer le contexte d’aide**.

**Métadonnées de contenu**

Dans le tableau suivant, toute chaîne apparaissant entre crochets est un espace réservé qui doit être remplacé par une valeur reconnue. Par exemple, dans \<meta name="Microsoft.Help.Locale" content="[language code]" /> , « [Language code] » doit être remplacé par une valeur telle que « en-US ».

| Property (représentation HTML) | Description |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Définit des paramètres régionaux pour cette rubrique. Si cette balise est utilisée dans une rubrique, elle doit être utilisée une seule fois et elle doit être insérée au-dessus de toute autre balise d’aide Microsoft. Si cette balise n’est pas utilisée, le corps du texte de la rubrique est indexé à l’aide de l’analyseur lexical associé aux paramètres régionaux du produit, s’il est spécifié ; dans le cas contraire, l’analyseur lexical en-US est utilisé. Cette balise est conforme à la norme ISOC RFC 4646. Pour garantir le bon fonctionnement de l’aide de Microsoft, utilisez cette propriété à la place de l’attribut de langage général. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Définit des paramètres régionaux pour cette rubrique lorsque d’autres paramètres régionaux sont également utilisés. Si cette balise est utilisée dans une rubrique, elle ne doit être utilisée qu’une seule fois. Utilisez cette balise lorsque le catalogue contient du contenu dans plusieurs langues. Plusieurs rubriques d’un catalogue peuvent avoir le même ID, mais chacune d’elles doit spécifier un TopicLocale unique. La rubrique qui spécifie un TopicLocale qui correspond aux paramètres régionaux du catalogue est celle qui est affichée dans la table des matières. Toutefois, toutes les versions linguistiques de la rubrique s’affichent dans les résultats de la recherche. |
| \< title>Bonhomme\</title> | Spécifie le titre de cette rubrique. Cette balise est requise et ne doit être utilisée qu’une seule fois dans une rubrique. Si le corps de la rubrique ne contient pas de section de titre \<div> , ce titre est affiché dans la rubrique et dans la table des matières. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Spécifie le texte d’un lien qui est affiché dans le volet index de la visionneuse d’aide. Lorsque l’utilisateur clique sur le lien, la rubrique s’affiche. Vous pouvez spécifier plusieurs mots clés d’index pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que des liens vers cette rubrique s’affichent dans l’index. Les mots clés « K » des versions antérieures de l’aide peuvent être convertis dans cette propriété. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Définit l’identificateur pour cette rubrique. Cette balise est requise et ne doit être utilisée qu’une seule fois dans une rubrique. L’ID doit être unique parmi les rubriques du catalogue qui ont les mêmes paramètres régionaux. Dans une autre rubrique, vous pouvez créer un lien vers cette rubrique à l’aide de cet ID. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Spécifie le mot clé F1 pour cette rubrique. Vous pouvez spécifier plusieurs mots clés F1 pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que cette rubrique soit affichée quand un utilisateur de l’application appuie sur la touche F1. En règle générale, un seul mot clé F1 est spécifié pour une rubrique. Les mots clés « F » des versions antérieures de l’aide peuvent être convertis dans cette propriété. |
| \< meta name="Description" content="[topic description]" /> | Fournit un bref résumé du contenu de cette rubrique. Si cette balise est utilisée dans une rubrique, elle ne doit être utilisée qu’une seule fois. Cette propriété est accessible directement par la bibliothèque de requêtes ; elle n’est pas stockée dans le fichier d’index. |
| Meta Name = "Microsoft. Help. TocParent" Content = "[parent_Id]"/> | Spécifie la rubrique parente de cette rubrique dans la table des matières. Cette balise est requise et ne doit être utilisée qu’une seule fois dans une rubrique. La valeur est le Microsoft.Help.Id du parent. Une rubrique ne peut avoir qu’un seul emplacement dans la table des matières. « -1 » est considéré comme l’ID de la rubrique de la racine de la table des matières. Dans [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] , cette page est la page d’informations de la visionneuse d’aide. C’est la même raison que nous ajoutons spécifiquement TocParent =-1 à certaines rubriques pour vous assurer qu’elles s’affichent au niveau supérieur. La page d’origine de la visionneuse d’aide est une page système qui n’est pas remplaçable. Si un VSP tente d’ajouter une page avec un ID de-1, il peut être ajouté au jeu de contenu, mais la visionneuse d’aide utilise toujours la page d’affichage de la visionneuse d’aide des pages système |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Spécifie l’endroit où cette rubrique apparaît dans la table des matières relative à ses rubriques homologues. Cette balise est requise et ne doit être utilisée qu’une seule fois dans une rubrique. La valeur est un entier. Une rubrique qui spécifie un entier de valeur inférieure s’affiche au-dessus d’une rubrique qui spécifie un entier de valeur supérieure. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Spécifie le produit que cette rubrique décrit. Si cette balise est utilisée dans une rubrique, elle ne doit être utilisée qu’une seule fois. Ces informations peuvent également être fournies en tant que paramètre transmis à l’indexeur de l’aide. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Spécifie la version du produit décrite dans cette rubrique. Si cette balise est utilisée dans une rubrique, elle ne doit être utilisée qu’une seule fois. Ces informations peuvent également être fournies en tant que paramètre transmis à l’indexeur de l’aide. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Utilisé par les produits pour identifier les sous-sections du contenu. Vous pouvez identifier plusieurs sous-sections pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que les liens identifient des sous-sections. Cette balise est utilisée pour stocker les attributs des Ciblesos et TargetFrameworkMoniker lorsqu’une rubrique est convertie à partir d’une version antérieure de l’aide. Le format du contenu est AttributeName : AttributeValue. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Spécifie cette version de la rubrique lorsque plusieurs versions existent dans un catalogue. Étant donné qu’il n’est pas garanti que Microsoft.Help.Id soit unique, cette balise est requise lorsque plusieurs versions d’une rubrique existent dans un catalogue, par exemple, lorsqu’un catalogue contient une rubrique pour la .NET Framework 3,5 et une rubrique pour le .NET Framework 4 et les deux ont le même Microsoft.Help.Id. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Spécifie si cette rubrique utilise le package de personnalisation du gestionnaire de bibliothèque d’aide ou un package de personnalisation qui est spécifique à la rubrique. Cette balise doit être TRUE ou FALSe. Si la valeur est TRUE, le package de personnalisation pour la rubrique associée remplace le package de personnalisation défini lorsque le gestionnaire de bibliothèque d’aide démarre afin que la rubrique soit rendue comme prévu, même si elle diffère du rendu d’un autre contenu. Si la valeur est FALSe, la rubrique active est rendue en fonction du package de personnalisation défini au démarrage du gestionnaire de bibliothèque d’aide. Par défaut, le gestionnaire de bibliothèque d’aide suppose que la personnalisation automatique est définie sur false, sauf si la variable SelfBranded est déclarée comme TRUE ; par conséquent, il n’est pas nécessaire de déclarer \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>Créer un package de personnalisation

La version de Visual Studio inclut un certain nombre de produits Visual Studio différents, y compris les interpréteurs de fonctions intégrés et intégrés pour les partenaires Visual Studio.  Chacun de ces produits requiert un certain niveau de prise en charge de la personnalisation du contenu de l’aide basée sur les rubriques, propre au produit.  Par exemple, les rubriques Visual Studio doivent avoir une présentation cohérente, tandis que SQL Studio, qui encapsule le shell ISO, requiert sa propre personnalisation de contenu d’aide unique pour chaque rubrique.  Un partenaire de Shell intégré peut souhaiter que les rubriques d’aide se trouvent dans le contenu de l’aide du produit Visual Studio parent tout en conservant leur propre personnalisation de rubrique.

Les packages de personnalisation sont installés par le produit contenant la visionneuse d’aide.  Pour les produits Visual Studio :

- Un package de personnalisation de secours (Branding_ \<locale> . MShC) est installé dans la racine de l’application de la visionneuse d’aide 2,3 (par exemple : C:\Program Files (x86) \Microsoft Help Viewer\v2.3) par le module linguistique de la visionneuse d’aide.  Cette valeur est utilisée dans les cas où le package de personnalisation du produit n’est pas installé (aucun contenu n’a été installé) ou lorsque le package de personnalisation installé est endommagé.  Les éléments Visual Studio (logo et commentaires) sont ignorés quand le package de personnalisation de l’application racine de secours est utilisé.

- Quand le contenu Visual Studio est installé à partir du service de package de contenu, un package de personnalisation est également installé (pour le premier scénario d’installation de contenu).  En cas de mise à jour du package de personnalisation, la mise à jour est installée lors de l’action de mise à jour du contenu ou d’installation supplémentaire du package.

Le Microsoft Help Viewer prend en charge la personnalisation des rubriques en fonction des métadonnées de rubrique.

- Lorsque les métadonnées de rubrique définissent l’automarquage = true, affichez la rubrique telle quelle, ne faites rien (en ce qui concerne la personnalisation).

- Lorsque les métadonnées de rubrique définissent l’automarquage = false, utilisez le package de personnalisation associé à la valeur des métadonnées TopicVendor.

- Où les métadonnées de rubrique définissent Name = "Microsoft. Help. TopicVendor" Content = \< branding package name in vendor MSHA> , utilisez le package de personnalisation défini dans la valeur de contenu.

- Dans le catalogue Visual Studio, il existe une application prioritaire des packages de personnalisation.  La première personnalisation par défaut de Visual Studio est appliquée, puis, si elle est définie dans les métadonnées de la rubrique et prise en charge avec le package de personnalisation (tel que défini dans le MSHA d’installation), la personnalisation définie par le fournisseur est appliquée comme remplacement.

Les éléments de personnalisation appartiennent généralement à trois catégories principales :

- Éléments d’en-tête (exemples : lien de commentaires, texte d’exclusion conditionnelle, logo)

- Comportements de contenu (exemples : développer/réduire des éléments de texte de contrôle et des éléments d’extrait de code)

- Éléments de pied de page (exemple de copyright)

Les éléments considérés comme des éléments marqués sont (détaillés dans cette spécification) :

- Logo catalogue/produit (exemple, Visual Studio)

- Lien de commentaires et éléments de messagerie

- Texte d’exclusion de responsabilité

- Texte de Copyright

Les fichiers de prise en charge dans le package de personnalisation de la visionneuse d’aide Visual Studio incluent :

- Graphiques (logos, icônes, etc.)

- Fichiers de script de Branding.js prenant en charge les comportements de contenu

- Branding.xml-chaînes utilisées de manière cohérente dans le contenu du catalogue.  Remarque : pour les éléments de texte de localisation Visual Studio dans le branding.xml, incluez _locID = " \<unique value> "

- Personnalisation. CSS-définitions de style pour la cohérence des présentations

- Impression. CSS-définitions de style pour une présentation imprimée cohérente

Comme indiqué ci-dessus, les packages de personnalisation sont associés à la rubrique :

- Quand SelfBranded = false est défini dans les métadonnées, la rubrique hérite du package de personnalisation du catalogue

- Ou lorsque SelfBranded = false et qu’il existe un package de personnalisation unique défini dans le MSHA et disponible lors de l’installation du contenu

Pour les vsp qui implémentent des packages de personnalisation personnalisés (contenu VSP, SelfBranded = true), vous pouvez commencer par le package de personnalisation de secours (installé avec la visionneuse d’aide) et modifier le nom du fichier selon vos besoins.  Le \<locale> fichier Branding_. MShC est un fichier zip dont l’extension de fichier est remplacée par. MShC. par conséquent, il vous suffit de changer l’extension. MShC pour .zip et extraire le contenu.  Voir ci-dessous pour les éléments de package de personnalisation et modifier le cas échéant (par exemple, remplacez le logo par le logo VSP et la référence du logo dans le fichier Branding.xml, mettez à jour Branding.xml par informations spécifiques à VSP, etc.).

Une fois toutes les modifications effectuées, créez un fichier zip contenant les éléments de personnalisation souhaités et modifiez l’extension en. MShC.

Pour associer le package de personnalisation personnalisé, créez le MSHA, qui contient la référence au fichier de personnalisation de MShC avec le contenu MShC (contenant les rubriques).  Voir ci-dessous « MSHA » pour savoir comment créer un MSHA de base.

Le fichier Branding.xml contient une liste d’éléments utilisés pour restituer systématiquement des éléments spécifiques dans une rubrique lorsque la rubrique contient \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  La liste d’éléments Visual Studio dans le fichier Branding.xml est répertoriée ci-dessous.  Cette liste est destinée à être utilisée comme modèle pour les adopteurs ISO Shell, où ils modifient ces éléments (par exemple, le logo, les commentaires et les droits d’auteur) pour répondre à leurs propres besoins de personnalisation des produits.

Remarque : les variables notées par « {n} » ont des dépendances de code, la suppression ou la modification de ces valeurs entraînera des erreurs et éventuellement un blocage de l’application. Les identificateurs de localisation (exemple _locID = « CodeSnippet. n ») sont inclus dans le package de personnalisation de Visual Studio.

**Branding.xml**

| Élément | Description |
| - | - |
| Fonctionnalités : | **CollapsibleArea** |
| Utilisez : | Développer réduit le texte du contrôle de contenu |
| **Element** | **Valeur** |
| ExpandText | Développez |
| CollapseText | Réduire |
| Fonctionnalités : | **CodeSnippet** |
| Utilisez : | Texte de contrôle d’extrait de code.  Remarque : le contenu de l’extrait de code avec un espace insécable sera remplacé par espace. |
| **Element** | **Valeur** |
| CopyToClipboard | Copier dans le Presse-papiers |
| ViewColorizedText | Afficher les couleurs |
| CombinedVBTabDisplayLanguage | Visual Basic (exemple) |
| VBDeclaration | Déclaration |
| VBUsage | Utilisation |
| Fonctionnalités : | **Commentaires, pieds de page et logo** |
| Utilisez : | Fournissez un contrôle de commentaires pour que le client fournisse des commentaires sur la rubrique en cours par courrier électronique.  Texte de copyright du contenu.  Définition du logo. |
| **Element** | **Valeur (ces chaînes peuvent être modifiées pour répondre aux besoins de l’adoption de contenu.)** |
| Intellectuelle | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a href="{0}" {1}>Envoyer \</a> des commentaires sur cette rubrique à Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Fonctionnalités : | **Clause d’exclusion de responsabilité** |
| Utilisez : | Ensemble de exclusions spécifiques à la casse pour le contenu traduit par une machine. |
| **Element** | **Valeur** |
| MT_Editable | Cet article a été traduit par une machine. Si vous disposez d’une connexion Internet, sélectionnez Afficher cette rubrique en ligne pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_NonEditable | Cet article a été traduit par une machine. Si vous disposez d’une connexion Internet, sélectionnez Afficher cette rubrique en ligne pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_QualityEditable | Cet article a été traduit manuellement. Si vous disposez d’une connexion Internet, sélectionnez Afficher cette rubrique en ligne pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_QualityNonEditable | Cet article a été traduit manuellement. Si vous disposez d’une connexion Internet, sélectionnez Afficher cette rubrique en ligne pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_BetaContents | Cet article a été traduit par machine pour une version préliminaire. Si vous disposez d’une connexion Internet, sélectionnez Afficher cette rubrique en ligne pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_BetaRecycledContents | Cet article a été traduit manuellement pour une version préliminaire. Si vous disposez d’une connexion Internet, sélectionnez Afficher cette rubrique en ligne pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| Fonctionnalités : | **Élément LinkTable** |
| Utilisez : | Prise en charge des liens de rubriques en ligne |
| **Element** | **Valeur** |
| LinkTableTitle | Lier une table |
| TopicEnuLinkText | Affichez la version anglaise \</a> de cette rubrique qui est disponible sur votre ordinateur. |
| TopicOnlineLinkText | Afficher cette rubrique \<a href="{0}" {1}> en ligne\</a> |
| OnlineText | En ligne |
| Fonctionnalités : | **Contrôle audio vidéo** |
| Utilisez : | Éléments d’affichage et texte pour le contenu vidéo |
| **Element** | **Valeur** |
| MultiMediaNotSupported | Internet Explorer 9 ou version ultérieure doit être installé pour prendre en charge le {0} contenu. |
| VideoText | affichage de la vidéo |
| AudioText | streaming audio |
| OnlineVideoLinkText | \<p>Pour afficher la vidéo associée à cette rubrique, cliquez {0} \<a href="{1}"> {2} ici \</a> .\</p> |
| OnlineAudioLinkText | \<p>Pour écouter l’audio associé à cette rubrique, cliquez {0} \<a href="{1}"> {2} ici \</a> .\</p> |
| Fonctionnalités : | **Contrôle de contenu non installé** |
| Utilisez : | Éléments de texte (chaînes) utilisés pour le rendu des contentnotinstalled.htm |
| **Element** | **Valeur** |
| ContentNotInstalledTitle | Aucun contenu n’a été trouvé sur votre ordinateur. |
| ContentNotInstalledDownloadContentText | \<p>Pour télécharger du contenu sur votre ordinateur, \<a href="{0}" {1}> cliquez sur l’onglet gérer \</a> .\</p> |
| ContentNotInstalledText | \<p>Aucun contenu n’est installé sur votre ordinateur. Consultez votre administrateur pour l’installation du contenu de l’aide locale.\</p> |
| Fonctionnalités : | **Contrôle de rubrique introuvable** |
| Utilisez : | Éléments de texte (chaînes) utilisés pour le rendu des topicnotfound.htm |
| **Element** | **Valeur** |
| TopicNotFoundTitle | Impossible de trouver la rubrique demandée sur votre ordinateur. |
| TopicNotFoundViewOnlineText | \<p>La rubrique que vous avez demandée est introuvable sur votre ordinateur, mais vous pouvez \<a href="{0}" {1}> afficher la rubrique en ligne \</a> .\</p> |
| TopicNotFoundDownloadContentText | \<p>Consultez le volet de navigation pour obtenir des liens vers des rubriques similaires ou \<a href="{0}" {1}> cliquez sur l’onglet gérer \</a> pour télécharger du contenu sur votre ordinateur.\</p> |
| TopicNotFoundText | \<p>La rubrique que vous avez demandée est introuvable sur votre ordinateur.\</p> |
| Fonctionnalités : | **Contrôle endommagé de la rubrique** |
| Utilisez : | Éléments de texte (chaînes) utilisés pour le rendu des topiccorrupted.htm |
| **Element** | **Valeur** |
| TopicCorruptedTitle | Impossible d’afficher la rubrique demandée. |
| TopicCorruptedViewOnlineText | \<p>La visionneuse d’aide ne peut pas afficher la rubrique demandée. Il peut y avoir une erreur dans le contenu de la rubrique ou une dépendance du système sous-jacent.\</p> |
| Fonctionnalités : | **Contrôle de page d’hébergement** |
| Utilisez : | Texte qui prend en charge l’affichage du contenu du nœud de niveau supérieur de la visionneuse d’aide. |
| **Element** | **Valeur** |
| HomePageTitle | Page d’affichage de Help Viewer |
| HomePageIntroduction | \<p>Bienvenue dans le Microsoft Help Viewer, une source d’informations essentielle pour tous ceux qui utilisent les outils, produits, technologies et services de Microsoft. La visionneuse d’aide vous permet d’accéder à des informations de référence, des exemples de code, des articles techniques et bien plus encore. Pour trouver le contenu dont vous avez besoin, parcourez la table des matières, utilisez la recherche en texte intégral ou parcourez le contenu à l’aide de l’index de mots clés.\</p> |
| HomePageContentInstallText | \<p>\<br />Utilisez l' \<a href="{0}" {1}> onglet gérer \</a> le contenu pour effectuer les opérations suivantes : \<ul> \<li> Ajouter du contenu à votre ordinateur. \</li> \<li> Recherchez les mises à jour de votre contenu local. \</li> \<li> Supprimer le contenu de votre ordinateur.\</li>\</ul>\</p> |
| HomePageInstalledBooks | Documentation installée |
| HomePageNoBooksInstalled | Aucun contenu n’a été trouvé sur votre ordinateur. |
| HomePageHelpSettings | Paramètres du contenu de l’aide |
| HomePageHelpSettingsText | \<p>Votre paramètre actuel est l’aide locale. La visionneuse d’aide affiche le contenu que vous avez installé sur votre ordinateur. \<br /> Pour modifier la source du contenu de l’aide, dans la barre de menus de Visual Studio, choisissez \<span style="{0}"> aide, définir la préférence de l’aide \</span> .\<br />\</p> |
| Octet | Mo |

**branding.js**

Le fichier branding.js contient du code JavaScript utilisé par les éléments de personnalisation de la visionneuse d’aide de Visual Studio.  Vous trouverez ci-dessous une liste des éléments de personnalisation et de la fonction JavaScript de prise en charge.  Toutes les chaînes à localiser pour ce fichier sont définies dans la section « chaînes localisables » en haut de ce fichier.  Le fichier ICL a été créé pour les chaînes Loc au sein du fichier branding.js.

|**Fonctionnalité de personnalisation**|**Fonction JavaScript**|**Description**|
|-|-|-|
|Var...||Définir des variables|
|Obtient le langage du code utilisateur|setUserPreferenceLang|mappe un index # à un langage de code|
|Définir et récupérer des valeurs de cookie|getCookie, setCookie||
|Membre hérité|changeMembersLabel|Développer/réduire le membre hérité|
|Quand SelfBranded = false|onLoad|Lisez la chaîne de requête pour vérifier s’il s’agit d’une demande d’impression.  Définissez tous les CodeSnippets, pour concentrer l’onglet par défaut de l’utilisateur.  S’il s’agit d’une demande d’impression, définissez isPrinterFriendly sur true. Vérifiez le mode de contraste élevé.|
|Extrait de code|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|écrit tous les objets de contrôle réductibles dans la liste.|
||CA_Click|en fonction de l’état de la zone réductible, définit l’image et le texte à présenter|
|Contraste de la prise en charge du logo|isBlackBackground()|Appelé pour déterminer si l’arrière-plan est noir.  Précision uniquement lorsque le mode de contraste élevé est présent.|
||isHighContrast()|utiliser une étendue colorée pour détecter le mode de contraste élevé|
||onHighContrast (noir)|Appelé lorsque le contraste élevé est détecté|
|Fonctionnalité de LST|||
||addToLanSpecTextIdSet (ID)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet (lang)||
|Fonctionnalités multimédias|légende (début, fin, texte, style)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff (ID)||
||toSeconds (t)||
||getAllComments (nœud)||
||styleRectify (styleName, styleValue)||
||showCC (ID)||
||sous-titre (ID)||

**FICHIERS HTM**

Le package de personnalisation contient un ensemble de fichiers HTM qui prennent en charge des scénarios de communication des informations clés pour aider les utilisateurs du contenu, par exemple une page d’accueil contenant une section décrivant les jeux de contenu installés et des pages indiquant à l’utilisateur quand les rubriques sont introuvables dans l’ensemble de rubriques local. Ces fichiers HTM peuvent être modifiés par produit.  Les fournisseurs de l’interpréteur de commandes ISO sont en mesure de prendre le package de personnalisation par défaut et de modifier le comportement et le contenu de ces pages en fonction de leurs besoins.  Ces fichiers font référence à leur package de personnalisation respectif pour que les balises de personnalisation obtiennent le contenu correspondant à partir du fichier branding.xml.

|**File**|**Utilisation**|**Source de contenu affichée**|
|-|-|-|
|homepage.htm|Il s’agit d’une page qui affiche le contenu actuellement installé et tout autre message approprié à présenter à l’utilisateur sur son contenu.  Ce fichier contient l’attribut de métadonnées supplémentaire « Microsoft.Help.Id » content = « -1 » qui place ce contenu en haut de la table des matières locale.||
||<META_HOME_PAGE_TITLE_ADD/>|Branding.xml, balise \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml, balise \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml, balise \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Section de titre Branding.xml balise \<HomePageInstalledBooks> , les données générées à partir de l’application,  \<HomePageNoBooksInstalled> quand aucun livre n’est installé.|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|Section de titre Branding.xml balise \<HomePageHelpSettings> , texte de la section \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|Lorsqu’une rubrique existe dans le jeu local, mais pour une raison quelconque, ne peut pas être affichée (contenu endommagé).||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml, balise \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml, balise \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Lorsqu’une rubrique est introuvable dans le jeu de contenu local, ni disponible en ligne||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml, balise \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml, balise \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml, balise \<TopicNotFoundText>|
|contentnotinstalled.htm|Lorsqu’aucun contenu local n’est installé pour le produit.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml, balise \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml, balise \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml, balise \<ContentNotInstalledText>|

**Fichiers CSS**

Le package de personnalisation de la visionneuse d’aide Visual Studio contient deux fichiers CSS pour prendre en charge la présentation cohérente du contenu de l’aide de Visual Studio :

- Personnalisation. CSS : contient des éléments CSS pour le rendu où SelfBranded = false

- Printer. css-contient des éléments CSS pour le rendu où SelfBranded = false

Personnalisation des fichiers. CSS inclut les définitions pour la présentation de la rubrique Visual Studio (il est conseillé que le fichier. CSS de personnalisation contenu dans le Branding_ \<locale> . MShC du service de package puisse changer).

**Fichiers graphiques**

Le contenu Visual Studio affiche un logo Visual Studio, ainsi que d’autres graphiques.  La liste complète des fichiers graphiques dans le package de personnalisation de la visionneuse d’aide Visual Studio est indiquée ci-dessous.

|**File**|**Utilisation**|**Exemples**|
|-|-|-|
|clear.gif|Utilisé pour restituer la zone réductible||
|footer_slice.gif|Présentation du pied de page||
|info_icon.gif|Utilisé lors de l’affichage d’informations|Clause d'exclusion de responsabilité|
|online_icon.gif|Cette icône doit être associée à des liens en ligne.||
|tabLeftBD.gif|Utilisé pour restituer le conteneur d’extraits de code||
|tabRightBD.gif|Utilisé pour restituer le conteneur d’extraits de code||
|vs_logo_bk.gif|Utilisé pour les références de logo de contraste normal, telles que définies dans la balise Branding.xml \<LogoFileName> .  Pour les produits Visual Studio, le nom du logo est vs_logo_bk.gif.||
|vs_logo_wh.gif|Utilisé pour les références de logo à contraste élevé, comme défini dans Branding.xml balise \<LogoFileNameHC> .  Pour les produits Visual Studio, le nom du logo est vs_logo_wh.gif.||
|ccOff.png|Graphique de sous-titrage||
|ccOn.png|Graphique de sous-titrage||
|ImageSprite.png|Utilisé pour restituer la zone réductible|graphique développé ou réduit|

## <a name="deploy-a-set-of-topics"></a>Déployer un ensemble de rubriques

Il s’agit d’un didacticiel simple et rapide pour la création d’un jeu de déploiement de contenu de la visionneuse d’aide composé d’un fichier MSHA et de l’ensemble de fichiers CAB ou MSHCs contenant les rubriques. Le MSHA est un fichier XML qui décrit un ensemble de fichiers CAB ou MSHC. La visionneuse d’aide peut lire le MSHA pour obtenir une liste de contenu (le .CAB ou. Fichiers MSHC) disponibles pour l’installation locale.

Il s’agit uniquement d’une introduction qui décrit le schéma XML très élémentaire pour la visionneuse d’aide MSHA.  Voici un exemple d’implémentation en dessous de cette brève présentation et de l’exemple fichiers HelpContentSetup. MSHA.

Le nom du MSHA, dans le cadre de cette introduction, est fichiers HelpContentSetup. MSHA (le nom du fichier peut être tout, avec l’extension. MSHA). Fichiers HelpContentSetup. MSHA (exemple ci-dessous) doit contenir une liste des CAB ou MSHCs disponibles.  Le type de fichier doit être cohérent au sein du MSHA (ne prend pas en charge une combinaison de types de fichiers MSHA et CAB). Pour chaque CAB ou MShC, il doit y avoir un \<div class="package"> ... \</div> (Voir l’exemple ci-dessous).

Remarque : dans l’exemple d’implémentation ci-dessous, nous avons inclus le package de personnalisation. Cela est essentiel à inclure pour récupérer les éléments de rendu de contenu Visual Studio nécessaires et les comportements de contenu.

Exemple de fichier fichiers HelpContentSetup. MSHA : (Remplacez « nom du jeu de contenu 1 » et « nom du jeu de contenu 2 », etc. par vos noms de fichiers.)

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

1. Créer un dossier local, par exemple « C:\SampleContent »

2. Pour cet exemple, nous allons utiliser des fichiers MSHC pour contenir les rubriques.  Un MSHC est un fichier zip dont l’extension de fichier est passée de .zip à. MShC.

3. Créez le fichier fichiers HelpContentSetup. MSHA sous la forme d’un fichier texte (le bloc-notes a été utilisé pour créer le fichier) et enregistrez-le dans le dossier indiqué ci-dessus (Voir l’étape 1).

La classe « personnalisation » existe et est unique. Le MShC de personnalisation est inclus dans ce manuel afin que le contenu installé ait la personnalisation et que les comportements de contenu contenus dans le MSHCs aient les éléments de support appropriés contenus dans le package de personnalisation. Sans cela, des erreurs se produiront lorsque le système recherchera des éléments de support qui ne font pas partie du contenu extrait (installé).

Pour obtenir le package de personnalisation Visual Studio, copiez le fichier Branding_en-US. MShC dans C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ dans votre dossier de travail.

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

L’utilisation de et l’extension des étapes ci-dessus permettent à VSPs de déployer leurs jeux de contenu pour la visionneuse d’aide de Visual Studio.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Ajouter de l’aide au shell Visual Studio (intégré et isolé)

**Introduction**

Cette procédure pas à pas montre comment incorporer du contenu d’aide dans une application de Shell Visual Studio, puis comment la déployer.

**Configuration requise**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Redistribution de Shell isolé Visual Studio 2013](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Vue d'ensemble**

L' [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] interpréteur de commandes est une version de l' [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE sur laquelle vous pouvez baser une application. De telles applications contiennent l’interpréteur de commandes isolé avec les extensions que vous créez. Utilisez les modèles de projet Shell isolé, inclus dans le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Kit de développement logiciel (SDK), pour générer des extensions.

Les étapes de base pour créer une application basée sur un interpréteur de commandes isolé et son aide :

1. Obtenez le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] package redistribuable ISO Shell (téléchargement Microsoft).

2. Dans Visual Studio, créez une extension d’aide basée sur l’interpréteur de commandes isolé, par exemple, l’extension d’aide contoso décrite plus loin dans cette procédure pas à pas.

3. Encapsulez l’extension et le package redistribuable ISO Shell dans un MSI de déploiement (une installation d’application). Cette procédure pas à pas n’inclut pas d’étape de configuration.

Créez un magasin de contenu Visual Studio. Pour le scénario d’interpréteur de commandes intégré, remplacez Visual Studio12 par le nom du catalogue de produits comme suit :

- Créer un dossier C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Créez un fichier nommé CatalogType.xml et ajoutez-le au dossier. Le fichier doit contenir les lignes de code suivantes :

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Définissez le magasin de contenu dans le registre. Pour l’interpréteur de commandes intégré, remplacez VisualStudio15 par le nom du catalogue de produits :

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Clé : LocationPath valeur de chaîne : C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Clé : valeur de chaîne nomcatalogue : [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentation

**Créer le projet**

Pour créer une extension de Shell isolée :

1. Dans Visual Studio, sous **fichier**, choisissez **nouveau projet**, sous **autres types de projets** , choisissez **extensibilité**, puis sélectionnez  **Visual Studio Shell isolé**. Nommez le projet `ContosoHelpShell` ) pour créer un projet d’extensibilité basé sur le modèle Visual Studio isolated Shell.

2. Dans Explorateur de solutions, dans le projet ContosoHelpShellUI, dans le dossier fichiers de ressources, ouvrez ApplicationCommands. vsct. Assurez-vous que cette ligne est commentée (recherchez « No_Help ») : `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Appuyez sur la touche F5 pour compiler et exécuter **Debug**. Dans l’instance expérimentale de l’IDE de l’interpréteur de commandes isolé, choisissez le menu **aide** . Assurez-vous que les commandes **afficher l’aide**, **Ajouter et supprimer le contenu d’aide** et **définir les préférences d’aide** s’affichent.

4. Dans Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier de personnalisation de l’interpréteur de commandes, ouvrez ContosoHelpShell. pkgdef. Pour définir le catalogue d’aide de contoso, ajoutez les lignes suivantes :

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Dans Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier de personnalisation de l’interpréteur de commandes, ouvrez ContosoHelpShell. application. pkgdef. Pour activer l’aide F1, ajoutez les lignes suivantes :

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

6. Dans Explorateur de solutions, dans le menu contextuel de la solution ContosoHelpShell, choisissez l’élément de menu **Propriétés** . Sous **Propriétés de configuration**, sélectionnez **Configuration Manager**. Dans la colonne **configuration** , remplacez chaque valeur « Debug » par « Release ».

7. Générez la solution. Cela crée un ensemble de fichiers dans un dossier Release, qui sera utilisé dans la section suivante.

Pour tester cela comme si elle était déployée :

1. Sur l’ordinateur sur lequel vous déployez contoso, installez l’interpréteur de commandes ISO téléchargé (à partir de l’image ci-dessus).

2. Créez un dossier dans \\ \Program Files (x86) \\ et nommez-le `Contoso` .

3. Copiez le contenu du dossier ContosoHelpShell Release dans le \\ dossier \Program Files (x86) \Contoso\.

4. Démarrez l’éditeur du registre en sélectionnant  **exécuter** dans le menu **Démarrer** et en entrant `Regedit` . Dans l’éditeur du Registre, choisissez **fichier**, puis **Importer**. Accédez au dossier du projet ContosoHelpShell. Dans le sous-dossier ContosoHelpShell, choisissez ContosoHelpShell. reg.

5. Créer un magasin de contenu :

    Pour ISO Shell-créer un magasin de contenu contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    Pour l' [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] interpréteur de commandes intégré, créez le dossier C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Créez CatalogType.xml et ajoutez au magasin de contenu (étape précédente) contenant :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Ajoutez les clés de Registre suivantes :

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key : valeur de chaîne LocationPath :

    Pour l’interpréteur de commandes ISO :

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Interpréteur de commandes intégré :

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Clé : valeur de chaîne nomcatalogue : [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentation. Pour le shell ISO, il s’agit du nom de votre catalogue.

8. Copiez votre contenu (CAB ou MSHC et MSHA) dans un dossier local.

9. Exemple de ligne de commande de l’interpréteur de commandes intégré pour tester le magasin de contenu. Pour l’interpréteur de commandes ISO, modifiez les valeurs Catalog et launchingApp comme il convient pour qu’elles correspondent au produit.

     « C:\Program Files (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe «/catalogName VisualStudio15/helpQuery Method = » page&ID = ContosoTopic0»/launchingApp Microsoft, VisualStudio, 12.0

10. Lancez l’application Contoso (à partir de la racine de l’application Contoso). Dans l’interpréteur de commandes ISO, choisissez l’élément de menu **aide** , puis modifiez la **préférence définir l’aide** pour **utiliser l’aide locale**.

11. Dans l’interpréteur de commandes, choisissez l’élément de menu **aide** , puis **afficher l’aide**. La visionneuse d’aide locale doit être lancée. Choisissez l’onglet **gérer le contenu** . Sous **source d’installation**, sélectionnez la case d’option **disque** . Cliquez sur le bouton **...** et accédez au dossier local contenant le contenu contoso (copié dans le dossier local à l’étape ci-dessus). Choisissez fichiers HelpContentSetup. MSHA. Contoso doit maintenant apparaître comme un livre dans les sélections de livres. Choisissez **Ajouter**, puis cliquez sur le bouton **mettre à jour** (coin inférieur droit).

12. Dans l’environnement de développement intégré (IDE) contoso, choisissez la touche F1 pour tester les fonctionnalités F1.

## <a name="additional-resources"></a>Ressources supplémentaires

Pour l’API du runtime, consultez [API de l’aide Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Pour plus d’informations sur l’utilisation de l’API d’aide, consultez Exemples de code de la [visionneuse d’aide](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Vous pouvez envoyer des suggestions de fonctionnalités à la [communauté des développeurs](https://aka.ms/feedback/suggest?space=8).
