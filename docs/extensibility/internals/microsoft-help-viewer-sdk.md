---
title: Microsoft Help Viewer SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b0e50c54aa702fb05732a37b3b363b378fe9c3a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087831"
---
# <a name="microsoft-help-viewer-sdk"></a>Kit SDK de Microsoft Help Viewer

Cet article contient les tâches suivantes pour les intégrateurs de la visionneuse d’aide Visual Studio :

- Création d’une rubrique (prise en charge de la touche F1)

- Création d’un package de contenu de la personnalisation de Help Viewer

- Déploiement d’un ensemble d’articles

- Ajout d’aide pour l’interpréteur de commandes de Visual Studio (intégré ou isolé)

- Ressources supplémentaires

## <a name="create-a-topic-f1-support"></a>Créer une rubrique (prise en charge de la touche F1)

Cette section fournit une vue d’ensemble des composants d’une rubrique présentée, exigences de rubrique, une brève description de la création d’une rubrique (y compris les exigences de prise en charge de F1) et enfin, une rubrique d’exemple avec son résultat du rendu.

**Vue d’ensemble de la rubrique visionneuse aide**

Lorsqu’une rubrique est appelée pour le rendu, la visionneuse d’aide Obtient les éléments de package de marque qui sont associés à la rubrique au moment de l’installation ou de la dernière mise à jour, ainsi que la rubrique XHTML et combine les deux pour entraîner l’affichage du contenu présenté (personnalisation des données + données de la rubrique).  Le package de marque contient des logos, prise en charge des comportements de contenu et le texte de personnalisation (droits d’auteur, etc.).  Voir « Création de Package de personnalisation » ci-dessous pour plus d’informations sur les éléments de package de marque.  En cas d’aucun package de personnalisation associé à la rubrique, la visionneuse d’aide utilisera le package de marque secours situé dans la racine de l’application visionneuse d’aide (Branding_en US.mshc).

**Aider les exigences de rubrique de visionneuse**

Pour être rendue correctement dans la visionneuse d’aide, le contenu de la rubrique brutes doit être XHTML 1.1 de la base W3C.

En règle générale, une rubrique contient deux sections :

- Métadonnées (voir le contenu de référence de métadonnées) : ID de nœud, etc. parent pour les données sur le sujet, par exemple, l’ID unique de la rubrique, la valeur du mot clé, l’ID de la table des matières, de la rubrique.

- Corps de contenu : conforme à XHTML 1.1 de la base W3C, qui inclut pris en charge les comportements de contenu (zone réductible, extrait de code, etc. Obtenir la liste complète ci-dessous).

Package de personnalisation de Visual Studio prises en charge les contrôles :

- Liens

- CodeSnippet

- CollapsibleArea

- Membre hérité

- LanguageSpecificText

Chaînes de langue prise en charge (non sensible à la casse) :

- javascript

- CSharp ou c#

- cplusplus ou Visual c++ ou c ++

- jscript

- Visual Basic ou Visual Basic

- f # ou fsharp ou fs

- autre - chaîne qui représente un nom de langage

**Création d’une rubrique de la visionneuse d’aide**

Créer un document XHTML nommé ContosoTopic4.htm et inclure la balise de titre (ci-dessous).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Ensuite, ajoutez des données pour définir la manière dont la rubrique doit être présenté (self marque ou non), comment référencer cette rubrique pour F1, dans lequel cette rubrique existe dans la table des matières, son ID (pour les références de lien par les autres rubriques), etc. Consultez le tableau « Métadonnées de contenu » ci-dessous pour une liste complète des métadonnées prises en charge.

- Dans ce cas, nous allons utiliser notre propre package de personnalisation, une variante du package de personnalisation de Visual Studio Help Viewer.

- Ajouter le nom de métadonnées de la touche F1 et la valeur (contenu de « Microsoft.Help.F1 » = « ContosoTopic4 ») qui correspondra à la valeur de F1 fournie dans le sac de l’IDE. (Voir la section prise en charge de la touche F1 pour plus d’informations.) C’est la valeur qui est mis en correspondance avec la touche F1 appeler à partir de l’IDE pour afficher cette rubrique quand F1 est sélectionnée dans l’IDE.

- Ajouter l’ID de rubrique. Il s’agit de la chaîne qui est utilisée par les autres rubriques pour lier à cette rubrique. Il est l’ID visionneuse d’aide pour cette rubrique.

- Pour la table des matières, ajoutez le nœud du parent de cette rubrique pour définir l’emplacement de ce nœud de table des matières de rubrique.

- Pour la table des matières, ajoutez l’ordre des nœuds de cette rubrique. Lorsque le nœud parent a `n` nombre des enfants nœuds, définir, dans l’ordre des nœuds enfants, emplacement de cette rubrique. Par exemple, cette rubrique est numéro 4 de 4 rubriques enfants.

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

Le corps (sans l’en-tête et le pied de page) de la rubrique contient des liens de page, une section Remarque, une zone réductible, un extrait de code et une section du langage spécifique.  Consultez la section Personnalisation pour plus d’informations sur ces zones de la rubrique présentée.

1. Ajouter une balise de titre de rubrique :  `<div class="title">Contoso Topic 4</div>`

2. Ajoutez une section Remarque : `<div class="alert"> add your table tag and text </div>`

3. Ajoutez une zone réductible :  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Ajouter un extrait de code :  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Ajouter du texte spécifiques au langage de code :  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Notez que `devLangnu=` vous permet d’entrer d’autres langages. Par exemple, `devLangnu="Fortran"` affiche Fortran lors de l’extrait de code DisplayLanguage = Fortran

6. Ajouter des liens de page : `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Remarque : pour non-langue prise en charge nouveau « Affichage » (exemple, F#, Cobol, Fortran) la colorisation de code dans l’extrait de code sera monochrome.

**Exemple aide visionneuse rubrique** le code illustre comment définir des métadonnées, un extrait de code, une zone réductible et le texte de langage spécifique.

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

**Prise en charge de la touche F1**

Dans Visual Studio, en sélectionnant F1 génère des valeurs fournies à partir de la position du curseur dans l’IDE et remplit un « jeu de propriétés » avec les valeurs fournies (basé sur l’emplacement du curseur. Lorsque le curseur se trouve au-dessus de la fonctionnalité x, la fonctionnalité x est active/dans le focus et remplit le sac de propriétés avec des valeurs.  Lors de la touche F1 est sélectionné le sac de propriétés est rempli et code de Visual Studio F1 visant à déterminer si la source d’aide les clients par défaut est local ou en ligne (en ligne est la valeur par défaut), puis crée la chaîne appropriée basée sur les utilisateurs de définition (en ligne est la valeur par défaut) - d’exécution (voir le Guide de l’administrateur aide pour les exe les paramètres de lancement) avec les paramètres de la visionneuse d’aide locale + ou les mots clés du conteneur de propriétés si aide locale est la valeur par défaut, ou l’URL MSDN avec le mot clé dans la liste de paramètres.

Si trois chaînes sont retournés pour F1, appelée pour sous forme de chaîne à valeurs multiples, prendre le premier terme, recherchez pour effectuer un test, et si trouvé, nous avons fini ; dans le cas contraire, passez à la chaîne suivante.  Ordre est important. Présentation des mots clés à valeurs multiples doit être une chaîne la plus longue chaîne plus courte.  Pour vérifier cela dans le cas pour les mots clés à valeurs multiples, examinez la chaîne d’URL de F1 en ligne, ce qui inclut le mot clé choisi.

Dans Visual Studio 2012, nous avons intentionnellement apporté une division plus forte entre en ligne et hors connexion, afin que si le paramètre de l’utilisateur a été pour Online, puis nous avons simplement transmis la F1 demande directement à notre service de requête en ligne sur MSDN, plutôt que d’acheminer via l’Agent de bibliothèque d’aide que nous avons dû dans Visual Studio 2010. Nous nous appuyons puis sur un état de « contenu fournisseur installé = true » pour déterminer s’il faut faire quelque chose de différent dans ce contexte. Si la valeur est true, nous effectuons ensuite cette logique d’analyse et de routage en fonction de ce que vous souhaitez prendre en charge pour vos clients. Si la valeur est false, puis nous sélectionnons à MSDN. Si l’utilisateur est Local, puis tous les appels dans le moteur d’aide locale.

F1 diagramme de flux :

![Flux F1](../../extensibility/internals/media/f1flow.png "F1flow")

Lorsque la source de contenu d’aide par défaut visionneuse d’aide est définie sur en ligne (lancement dans le navigateur) :

- Fonctionnalités de Visual Studio partenaire (VSP) émettent une valeur au sac de propriétés F1 (prefix.keyword sac de propriété et en ligne URL pour le préfixe dans le Registre) : F1 envoie une URL VSP + tous les paramètres dans le navigateur.

- Fonctionnalités de Visual Studio (éditeur de langage, les éléments de menu spécifiques de Visual Studio, etc.) :  F1 envoie une URL Visual Studio dans le navigateur.

Quand la source de contenu d’aide par défaut Help Viewer est définie à l’aide locale (lancement dans la visionneuse d’aide) :

- Fonctionnalités VSP où le mot clé correspondent entre sac F1 et des index de magasin local (autrement dit, le prefix.keyword du sac de propriété = valeur trouvée dans l’index de magasin local) :  F1 affiche la rubrique dans la visionneuse d’aide.

- Fonctionnalités de Visual Studio (aucune option pour le fichier VSP remplacer le jeu de propriétés émis à partir des fonctionnalités de Visual Studio) : F1 affiche une rubrique de Visual Studio dans la visionneuse d’aide.

Définissez les valeurs de Registre suivantes pour activer le fournisseur contenu d’aide F1 secours. F1 secours signifie que la visionneuse d’aide est définie pour rechercher d’aide F1 contenu en ligne, et le contenu de fournisseur est installé localement sur disque dur de l’utilisateur. La visionneuse d’aide doit ressembler à l’aide locale pour le contenu même si le paramètre par défaut est de l’aide en ligne.

1. Définir le **VendorContent** valeur sous la clé de Registre 2.3 aider à :

   - Pour les systèmes d’exploitation 32 bits :

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   - Pour les systèmes d’exploitation 64 bits :

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

2. Enregistrer l’espace de noms de partenaire sous la clé de Registre 2.3 aider à :

   - Pour les systèmes d’exploitation 32 bits :

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em>\\<namespace\></em>

      "location"="offline"

   - Pour les systèmes d’exploitation 64 bits :

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em>\\<namespace\></em>

      "location"="offline"

**Namespace natif d’analyse de base**

Pour activer l’analyse de base espace de noms natif, dans le Registre, ajoutez un nouveau DWORD par le nom de : BaseNativeNamespaces et définissez sa valeur sur 1 (sous la clé de catalogue qu’ils souhaitent prendre en charge).  Par exemple, si vous souhaitez utiliser le catalogue de Visual Studio, vous pouvez ajouter la clé pour le chemin d’accès :

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Lorsqu’un mot clé F1 dans le format de QU'EN-TÊTE/méthode est rencontrée, le caractère '/' sera analysé, ce qui entraîne la construction suivante :

- EN-tête : sera l’espace de noms peut être utilisé pour inscrire dans le Registre

- MÉTHODE : cela deviendra le mot clé qui est transmis.

Par exemple, étant donné une bibliothèque personnalisée appelée CustomLibrary et une méthode appelée MyTestMethod, quand un F1 demande arrive qu’il contient seront au format `CustomLibrary/MyTestMethod`.

Un utilisateur peut inscrire CustomLibrary en tant que l’espace de noms sous la ruche de partenaires, puis fournir toute clé emplacement ils le souhaitent, et le mot clé transmis à la requête sera MyTestMethod.

**Activer l’aide de l’outil dans l’IDE de débogage**

Ajoutez la clé de Registre suivante et la valeur :

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Valeur : Affichage des résultats de débogage dans les données de vente au détail : OUI

Dans l’IDE, sous l’élément de menu Aide, sélectionnez **contexte de vous aider à déboguer**.

**Métadonnées de contenu**

Dans le tableau suivant, n’importe quelle chaîne qui s’affiche entre crochets est un espace réservé qui doit être remplacé par une valeur reconnue. Par exemple, dans \<meta name="Microsoft.Help.Locale » contenu = « [code de langue] » / >, « [code de langue] » doit être remplacé par une valeur comme « en-us ».

| Propriété (représentation HTML) | Description |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Définit les paramètres régionaux pour cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois et doit être insérée au-dessus de toutes les autres balises de Microsoft Help. Si cette balise n’est pas utilisée, le texte du corps de la rubrique est indexé à l’aide du séparateur de mots qui est associé avec le paramètres régionaux du produit, s’il est spécifié ; Sinon, l’en-us lexical est utilisé. Cette balise est conforme à la norme RFC 4646 ISOC. Pour vous assurer que Microsoft Help fonctionne correctement, utilisez cette propriété au lieu de l’attribut de langue général. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Définit les paramètres régionaux pour cette rubrique lorsque d’autres paramètres régionaux est également utilisés. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Utilisez cette balise lorsque le catalogue contient le contenu dans plusieurs langues. Plusieurs rubriques dans un catalogue peuvent avoir le même ID, mais chacun doit spécifier un TopicLocale unique. La rubrique qui spécifie un TopicLocale qui correspond aux paramètres régionaux du catalogue est de la rubrique qui s’affiche dans la table des matières. Toutefois, toutes les versions linguistiques de la rubrique sont affichées dans les résultats de la recherche. |
| \< titre > [Title] \< /title > | Spécifie le titre de cette rubrique. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. Si le corps de la rubrique ne contient pas un titre \<div > section, ce titre s’affiche dans la rubrique et dans la table des matières. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Spécifie le texte d’un lien qui s’affiche dans le volet de l’index de la visionneuse d’aide. Un clic sur le lien, la rubrique s’affiche. Vous pouvez spécifier plusieurs mots clés d’index pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que des liens vers cette rubrique apparaissent dans l’index. Mots clés « K » à partir de versions antérieures de l’aide peuvent être convertis en cette propriété. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Définit l’identificateur pour cette rubrique. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. L’ID doit être unique parmi les rubriques dans le catalogue qui ont les mêmes paramètres régionaux. Dans une autre rubrique, vous pouvez créer un lien vers cette rubrique à l’aide de ce code. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Spécifie le mot clé F1 pour cette rubrique. Vous pouvez spécifier plusieurs mots clés F1 pour une rubrique, ou vous pouvez omettre cette balise si vous ne voulez pas de cette rubrique à afficher lorsque l’utilisateur d’une application appuie sur F1. En règle générale, qu’une seule de mot clé F1 est spécifié pour une rubrique. Mots clés « F » à partir de versions antérieures de l’aide peuvent être convertis en cette propriété. |
| \< meta name="Description" content="[topic description]" /> | Fournit un bref résumé du contenu dans cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Cette propriété est accessible directement par la bibliothèque de la requête ; Il n’est pas stocké dans le fichier d’index. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Spécifie la rubrique parente de cette rubrique dans la table des matières. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. La valeur est le Microsoft.Help.Id du parent. Une rubrique peut avoir qu’un seul emplacement dans la table des matières. « -1 » est considéré comme l’ID de rubrique pour la racine de la table des matières. Dans [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], cette page est la page d’accueil visionneuse d’aide. Il s’agit de la même raison, que plus précisément, nous ajouter TocParent =-1 à certaines rubriques pour vous assurer que lorsqu’ils apparaissent en haut niveau. La page d’accueil visionneuse d’aide est une page de système et par conséquent, non remplaçables. Si un VSP essaie d’ajouter une page avec un ID de -1, il peut obtenir ajouté à l’ensemble de contenu, mais visionneuse d’aide sera toujours utiliser la page system - accueil visionneuse d’aide |
| \< contenu de métadonnées name="Microsoft.Help.TocOrder » = « [entier] » / > | Spécifie l’emplacement dans la table des matières de cette rubrique par rapport à ses rubriques homologue. Cette balise est obligatoire et doit être utilisée qu’une seule fois dans une rubrique. La valeur est un entier. Une rubrique qui spécifie un entier de faible valeur s’affiche au-dessus d’une rubrique qui spécifie un entier de valeur plus élevée. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Spécifie le produit qui décrit cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Ces informations peuvent également être fournies en tant que paramètre qui est passé à l’indexeur d’aide. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Spécifie la version du produit qui décrit cette rubrique. Si cette balise est utilisée dans une rubrique, il doit être utilisé qu’une seule fois. Ces informations peuvent également être fournies en tant que paramètre qui est passé à l’indexeur d’aide. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Utilisé par les produits pour identifier les sous-sections de contenu. Vous pouvez identifier plusieurs sous-sections pour une rubrique, ou vous pouvez omettre cette balise si vous ne souhaitez pas que des liens pour identifier les sous-sections. Cette balise est utilisée pour stocker les attributs pour TargetOS et TargetFrameworkMoniker lorsqu’une rubrique est convertie à partir d’une version antérieure de l’aide. Le format du contenu est AttributeName:AttributeValue. |
| \< contenu de name="Microsoft.Help.TopicVersion Meta = « [rubrique version number] » / > | Spécifie cette version de la rubrique lorsque plusieurs versions existent dans un catalogue. Étant donné que Microsoft.Help.Id n’est pas garanti pour être unique, cette balise est requise lorsque plusieurs versions d’une rubrique existent dans un catalogue, par exemple, lorsqu’un catalogue contient une rubrique pour le .NET Framework 3.5 et une rubrique pour le .NET Framework 4 et les deux ont la même Micro réversible. Help.Id. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Indique si cette rubrique utilise le package de marque de démarrage de gestionnaire de bibliothèque d’aide ou d’un package de personnalisation est spécifique à la rubrique. Cette balise doit avoir la valeur TRUE ou FALSE. Si la valeur est TRUE, le package de personnalisation pour la rubrique associée remplace le package de personnalisation est défini lorsque le Gestionnaire de bibliothèque d’aide démarre afin que la rubrique est restituée comme prévu même si elle diffère du rendu d’un autre contenu. Si la valeur est FALSE, la rubrique actuelle est affichée en fonction de package de personnalisation qui est défini au démarrage du Gestionnaire de bibliothèque d’aide. Par défaut, le Gestionnaire de bibliothèque d’aide suppose automatique marque avoir la valeur false, sauf si la variable SelfBranded est déclarée en tant que la valeur est TRUE ; Par conséquent, il est inutile de déclarer \<nom meta = « SelfBranded » content = « FALSE » / >. |

## <a name="create-a-branding-package"></a>Créer un package de marque

La version de Visual Studio comprend un nombre de différents produits Visual Studio, y compris l’isolé et les interpréteurs de commandes intégrés pour les partenaires Visual Studio.  Chacun de ces produits nécessite une certaine mesure basée sur une rubrique de contenu d’aide prise en charge, unique pour le produit de personnalisation.  Par exemple, les rubriques de Visual Studio doivent disposer une présentation de la marque cohérente, tandis que SQL Studio, qui encapsule l’interpréteur de commandes ISO, nécessite son propre contenu unique aide marque pour chaque rubrique.  Un partenaire de Shell intégré souhaiterez peut-être les rubriques d’aide à être dans le contenu d’aide de Visual Studio produit parent tout en conservant leur propre personnalisation de la rubrique.

Personnalisation de packages est installée par le produit contenant la visionneuse d’aide.  Pour les produits Visual Studio :

- Un package de marque de secours (Branding_\<paramètres régionaux > .mshc) est installé dans la racine de l’application aide les 2.3 de visionneuse (exemple : C:\Program fichiers (x86) \Microsoft Help Viewer\v2.3) par le module linguistique de visionneuse d’aide.  Cela est utilisé pour les cas où le produit marque le package n’est pas installé (aucun contenu n’a été installé) ou dans lequel le package de marque installé est endommagé.  Les éléments de Visual Studio (logo et des commentaires) sont ignorés lorsque le package de marque secours de racine d’application est utilisé.

- Lorsque le contenu de Visual Studio est installé à partir du service de package de contenu, un package de personnalisation est également installé (par le premier scénario de l’installation du contenu temps).  S’il existe une mise à jour le package de personnalisation, la mise à jour est installé lors de la prochaine mise à jour de contenu ou l’action d’installation de package supplémentaire se produit.

La visionneuse d’aide Microsoft prend en charge la personnalisation des rubriques en fonction des métadonnées de la rubrique.

- Où les métadonnées de la rubrique définissent self marque = true, afficher la rubrique en l’état, ne faites rien (en ce qui concerne la marque).

- Où les métadonnées de la rubrique définissent self marque = false, utiliser le package de marque associé à valeur de métadonnées TopicVendor.

- Contenu où les métadonnées de la rubrique définissent name="Microsoft.Help.TopicVendor » =\< marque nom du package dans le fournisseur MSHA >, utilisez le package de personnalisation défini dans la valeur de contenu.

- Dans le catalogue de Visual Studio, il existe une application de priorité des Packages de personnalisation.  Personnalisation de première Visual Studio par défaut est appliquée et puis, si définis dans les métadonnées de la rubrique et la prise en charge avec la personnalisation associée package (tel que défini dans l’installation msha), le défini par le fournisseur de personnalisation est appliqué comme un remplacement.

Éléments de personnalisation se répartissent généralement en trois catégories principales :

- Éléments d’en-tête (exemples lien commentaires, conditionnel dédit de responsabilité, logo)

- Contenu des comportements (exemples incluent les éléments de texte de contrôle Développer/réduire et éléments de l’extrait de code)

- Éléments de pied de page (par exemple, Copyright)

Éléments considérés comme incluent des éléments personnalisés (détaillée dans cette spécification) :

- Logo/produit du catalogue (par exemple, Visual Studio)

- Éléments de liaison et le courrier électronique des commentaires

- Dédit de responsabilité

- Texte de droits d’auteur

Fichiers de prise en charge dans le package de marque de Help Viewer de Visual Studio sont les suivantes :

- Graphiques (logos, icônes, etc.).

- Branding.js - prise en charge les comportements de contenu des fichiers de script

- Branding.XML - chaînes utilisé de manière cohérente sur le contenu du catalogue.  Remarque : pour inclure des éléments de texte de la localisation de Visual Studio dans le branding.xml, _locID = «\<valeur unique > »

- Branding.CSS - des définitions de style pour la cohérence de la présentation

- Printing.CSS - présentation imprimée cohérente des définitions de style

Comme indiqué ci-dessus, les Packages de personnalisation sont associés à la rubrique :

- Lorsque SelfBranded = false est définie dans les métadonnées, le catalogue de package de marque de hérite de la rubrique

- Ou lorsque SelfBranded = false et il est un Package de marque uniques défini dans le MSHA et disponible lorsque le contenu est installé

Pour vsp implémentation de packages de personnalisation personnalisées (contenu VSP, SelfBranded = True), la première consiste à continuer à démarrer avec le package de marque secours (installé avec la visionneuse d’aide), puis remplacez le nom du fichier comme il convient.  Le Branding_\<paramètres régionaux > .mshc fichier est un fichier zip avec l’extension de fichier passé à .mshc, il vous suffit de diffère de l’extension .mshc .zip et extrayez le contenu.  Voir ci-dessous pour les éléments de package de personnalisation et le modifier selon les besoins (par exemple, changer le logo pour le logo VSP et la référence pour le logo dans le fichier Branding.xml, mettre à jour Branding.xml par caractéristiques VSP, etc.).

Lorsque toutes les modifications sont effectuées, créez un fichier zip contenant les éléments de personnalisation souhaités et remplacez l’extension .mshc.

Pour associer le package de marque personnalisé, créez MSHA, qui contient la référence au fichier mshc personnalisation, ainsi que le contenu mshc (qui contient les rubriques).  Voir ci-dessous « MSHA » pour savoir comment créer une base MSHA.

Le fichier Branding.xml contient une liste d’éléments utilisés pour le rendu de manière cohérente des éléments spécifiques dans une rubrique lors de la rubrique contient \<meta name="Microsoft.Help.SelfBranded « contenu = « false » / >.  Vous trouverez ci-dessous la liste d’éléments dans le fichier Branding.xml Visual Studio.  Cette liste est destinée à être utilisée comme un modèle pour les utilisateurs précoces ISO Shell, où ils modifier ces éléments (par exemple logo, commentaires et le Copyright) pour répondre à leurs propres marque de produit a besoin.

Remarque : les variables indiqués par « {n} » ont des dépendances de code, suppression ou modification de ces valeurs entraîne des erreurs et, éventuellement, panne d’application. Identificateurs de localisation (exemple _locID="codesnippet.n ») sont inclus dans le Package de personnalisation de Visual Studio.

**Branding.xml**

| | |
| - | - |
| Fonctionnalités : | **CollapsibleArea** |
| Utiliser : | Développez le texte du contrôle de contenu est réduite |
| **Élément** | **Valeur** |
| ExpandText | Expand |
| CollapseText | Réduire |
| Fonctionnalités : | **CodeSnippet** |
| Utiliser : | Texte de contrôle l’extrait de code.  Remarque : Contenu d’extrait de code avec « Sans rupture » espace passera à l’espace. |
| **Élément** | **Valeur** |
| CopyToClipboard | Copier dans le Presse-papiers |
| ViewColorizedText | Affichage coloré |
| CombinedVBTabDisplayLanguage | Visual Basic (exemple) |
| VBDeclaration | Déclaration |
| VBUsage | Utilisation |
| Fonctionnalités : | **Commentaires, un pied de page et Logo** |
| Utiliser : | Fournir un contrôle de commentaires pour le client fournir des commentaires sur la rubrique actuelle par courrier électronique.  Texte de copyright pour le contenu.  Définition de logo. |
| **Élément** | **Valeur (ces chaînes peuvent être modifiées pour répondre aux besoins de l’utilisateur précoce de contenu.)** |
| CopyRight | © 2013 Microsoft Corporation. Tous droits réservés. |
| SendFeedback | \<un href = »{0}» {1}> envoyer des commentaires\</a > sur cette rubrique à Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Fonctionnalités : | **Exclusion de responsabilité** |
| Utiliser : | Le contenu traduit un ensemble de cas spécifique d’exclusion de responsabilité pour la machine. |
| **Élément** | **Valeur** |
| MT_Editable | Cet article a été traduit. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_NonEditable | Cet article a été traduit. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_QualityEditable | Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_QualityNonEditable | Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_BetaContents | Cet article a été traduites pour la version préliminaire. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_BetaRecycledContents | Cet article a été traduit manuellement pour la version préliminaire. Si vous avez une connexion Internet, sélectionnez « Afficher cette rubrique en ligne » pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| Fonctionnalités : | **LinkTable** |
| Utiliser : | Prise en charge des liens vers des rubriques en ligne |
| **Élément** | **Valeur** |
| LinkTableTitle | Table de liens |
| TopicEnuLinkText | Afficher la version anglaise\</a > de cette rubrique est disponible sur votre ordinateur. |
| TopicOnlineLinkText | Afficher cette rubrique \<un href = »{0}» {1}> en ligne\</a > |
| OnlineText | Online |
| Fonctionnalités : | **Contrôle Audio Video** |
| Utiliser : | Afficher les éléments et le texte pour le contenu vidéo |
| **Élément** | **Valeur** |
| MultiMediaNotSupported | Internet Explorer 9 ou version ultérieure doit être installé pour prendre en charge {0} contenu. |
| VideoText | affichage de vidéo |
| AudioText | diffusion en continu d’audio |
| OnlineVideoLinkText | \<p > pour afficher la vidéo de cette rubrique, cliquez sur {0} \<un href = »{1}« >{2}ici\</a >.\< /p > |
| OnlineAudioLinkText | \<p > pour écouter l’audio associé à cette rubrique, cliquez sur {0} \<un href = »{1}« >{2}ici\</a >.\< /p > |
| Fonctionnalités : | **Contrôle de contenu de pas installé** |
| Utiliser : | Éléments de texte (chaînes) utilisés pour le rendu de contentnotinstalled.htm |
| **Élément** | **Valeur** |
| ContentNotInstalledTitle | Aucun contenu n’a été trouvé sur votre ordinateur. |
| ContentNotInstalledDownloadContentText | \<p > pour télécharger du contenu sur votre ordinateur, \<un href = »{0}» {1}> cliquez sur l’onglet gérer\</a >.\< /p > |
| ContentNotInstalledText | \<p > aucun contenu n’est installé sur votre ordinateur. Consultez votre administrateur pour l’installation du contenu d’aide locale. \</p > |
| Fonctionnalités : | **Contrôle introuvable de rubrique** |
| Utiliser : | Éléments de texte (chaînes) utilisés pour le rendu de topicnotfound.htm |
| **Élément** | **Valeur** |
| TopicNotFoundTitle | Impossible de trouver la rubrique demandée sur votre ordinateur. |
| TopicNotFoundViewOnlineText | \<p > la rubrique que vous avez demandée est introuvable sur votre ordinateur, mais vous pouvez \<un href = »{0}» {1}> Afficher la rubrique en ligne\</a >.\< /p > |
| TopicNotFoundDownloadContentText | \<p > consultez le volet de navigation pour obtenir des liens vers des rubriques similaires ou \<un href = »{0}» {1}> cliquez sur l’onglet gérer\</a > pour télécharger du contenu sur votre ordinateur.\< /p > |
| TopicNotFoundText | \<p > la rubrique que vous avez demandée est introuvable sur votre ordinateur. \</p > |
| Fonctionnalités : | **Rubrique endommagé contrôle** |
| Utiliser : | Éléments de texte (chaînes) utilisés pour le rendu de topiccorrupted.htm |
| **Élément** | **Valeur** |
| TopicCorruptedTitle | Impossible d’afficher la rubrique demandée. |
| TopicCorruptedViewOnlineText | \<p > visionneuse d’aide ne peut pas afficher la rubrique demandée. Il peut y avoir une erreur dans le contenu de la rubrique ou une dépendance de système sous-jacent. \</p > |
| Fonctionnalités : | **Contrôle de la Page d’accueil** |
| Utiliser : | Texte prenant en charge l’affichage du contenu du nœud de niveau supérieur de visionneuse d’aide. |
| **Élément** | **Valeur** |
| HomePageTitle | Accueil visionneuse d’aide |
| HomePageIntroduction | \<p > Bienvenue dans la visionneuse d’aide Microsoft, une source incontournable des informations relatives à toute personne utilisant les outils, produits, technologies et services Microsoft. La visionneuse d’aide vous donne accès aux informations de référence et de procédure, exemple de code, des articles techniques et bien plus encore. Pour trouver le contenu que vous avez besoin, parcourez la table des matières, utilisez la recherche en texte intégral, ou parcourez le contenu à l’aide de l’index des mots clés. \</p > |
| HomePageContentInstallText | \<p >\<br / > Utilisez le \<un href = »{0}» {1}> Gérer le contenu\</a > onglet effectuer les opérations suivantes :\<ul >\<li > ajouter du contenu sur votre ordinateur.\< /li >\<li > vérifier les mises à jour à votre contenu local.\< /li >\<li > Supprimer le contenu de votre ordinateur.\< /li >\</ul >\</p > |
| HomePageInstalledBooks | Livres installés |
| HomePageNoBooksInstalled | Aucun contenu n’a été trouvé sur votre ordinateur. |
| HomePageHelpSettings | Paramètres de contenu d’aide |
| HomePageHelpSettingsText | \<p > votre paramètre actuel est aide locale. La visionneuse d’aide affiche le contenu que vous avez installée sur votre ordinateur. \<br / > pour modifier la source de contenu d’aide, dans la barre de menus de Visual Studio, choisissez \<span style = »{0}» > aide, définir les préférences pour aider à\</span >.\< br / >\</p > |
| MegaByte | MO |

**branding.js**

Le fichier branding.js contient JavaScript utilisé par les éléments de personnalisation de Visual Studio Help Viewer.  Voici une liste des éléments de personnalisation et de la fonction prise en charge de JavaScript.  Toutes les chaînes soient localisées pour ce fichier sont définies dans la section « Chaînes localisables » en haut de ce fichier.  Fichier ICL a été créé pour la localisation des chaînes dans le fichier branding.js.

||||
|-|-|-|
|**Fonctionnalité de personnalisation**|**Fonction JavaScript**|**Description**|
|Var...||Définir des variables|
|Obtenir le langage de code utilisateur|setUserPreferenceLang|mappe un index # pour le langage de code|
|Définir et obtenir les valeurs de cookie|getCookie, setCookie||
|Membre hérité|changeMembersLabel|Développer/réduire le membre hérité|
|When SelfBranded=False|onLoad|Lire la chaîne de requête pour vérifier s’il est une demande d’impression.  Définir tous les codesnippets concentrer l’onglet par défaut d’utilisateur.  Dans le cas d’une demande d’impression, puis définissez isPrinterFriendly sur true. Vérifier le mode de contraste élevé.|
|Extrait de code|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|écrire tous les objets de contrôle réductible dans la liste.|
||CA_Click|en fonction de l’état de la zone réductible, définit les textes pour présenter et images|
|Prise en charge de contraste de Logo|isBlackBackground()|Appelé pour déterminer si l’arrière-plan est noir.  Précise uniquement quand le mode contraste élevé.|
||isHighContrast()|utiliser une étendue de couleur pour le mode de contraste élevé de détection|
||onHighContrast(black)|Appelé lorsque le contraste élevé est détecté|
|Fonctionnalités LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Fonctionnalités multimédia|caption(begin, end, text, style)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||subtitle(id)||

**FICHIERS HTM**

Le package de personnalisation contient un ensemble de fichiers HTM qui prennent en charge des scénarios permettant de communiquer des informations de clé pour les utilisateurs de contenu technique, par exemple une page d’accueil qui contient une section décrivant les ensembles de contenu sont installés et les pages qui informe l’utilisateur lorsque les rubriques ne peut pas se trouve dans le jeu de rubriques local. Ces fichiers HTM peuvent être modifiés par produit.  Fournisseurs d’interpréteur de commandes ISO sont en mesure de prendre le package de marque par défaut et modifier le comportement et le contenu de ces pages à la suite de leurs besoins.  Ces fichiers font référence à leur package de marque respectif afin que les balises de personnalisation obtenir le contenu correspondant à partir du fichier branding.xml.

||||
|-|-|-|
|**Fichier**|**Utilisation**|**Affiche la Source de contenu**|
|homepage.htm|Il s’agit d’une page qui affiche le contenu actuellement installé et tout autre message appropriée à présenter à l’utilisateur sur leur contenu.  Ce fichier contient le contenu « Microsoft.Help.Id » de l’attribut de données supplémentaire meta = « -1 » qui place ce contenu en haut de la table des matières de contenu local.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.XML, balise \<HomePageTitle >|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.XML, balise \<HomePageIntroduction >|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.XML, balise \<HomePageContentInstallText >|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Titre de section Branding.xml balise\<HomePageInstalledBooks >, les données générées à partir de l’application, \<HomePageNoBooksInstalled > lorsque aucun livres ne sont installés.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Titre de section Branding.xml balise \<HomePageHelpSettings >, section texte \<HomePageHelpSettingsText >.|
|topiccorrupted.htm|Lorsqu’une rubrique existe dans le jeu local, mais pour une raison quelconque ne peut pas être affichée (endommagé contenu).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.XML, balise \<TopicCorruptedTitle >|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.XML, balise \<TopicCorruptedViewOnlineText >|
|topicnotfound.htm|Quand une rubrique est introuvable dans le contenu local défini ni disponible en ligne||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.XML, balise \<TopicNotFoundTitle >|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.XML, balise \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.XML, balise \<TopicNotFoundText >|
|contentnotinstalled.htm|Lorsqu’il n’existe pas de contenu local installé pour le produit.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.XML, balise \<ContentNotInstalledTitle >|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.XML, balise \<ContentNotInstalledDownloadContentText >|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.XML, balise \<ContentNotInstalledText >|

**Fichiers CSS**

Le Package Visual Studio aide visionneuse marque contient deux fichiers css pour prendre en charge de la présentation du contenu cohérente aide de Visual Studio :

- Branding.CSS - contient les éléments css pour le rendu where SelfBranded = false

- Printer.CSS - contient les éléments css pour le rendu where SelfBranded = false

Les fichiers branding.CSS incluent les définitions pour la présentation de rubrique Visual Studio (inconvénient est que le branding.css contenue dans le Branding_\<paramètres régionaux > .mshc à partir du service de package peut changer).

**Fichiers graphiques**

Contenu de Visual Studio affiche un logo de Visual Studio, ainsi que des autres graphiques.  Vous trouverez ci-dessous la liste complète des fichiers graphiques dans le package de marque de Help Viewer de Visual Studio.

||||
|-|-|-|
|**Fichier**|**Utilisation**|**Exemples**|
|clear.gif|Utilisé pour restituer la zone réductible||
|footer_slice.gif|Présentation de pied de page||
|info_icon.gif|Utilisé lors de l’affichage d’informations|Exclusion de responsabilité|
|online_icon.gif|Cette icône est à associer à des liens en ligne||
|tabLeftBD.gif|Utilisé pour restituer le conteneur d’extrait de code||
|tabRightBD.gif|Utilisé pour restituer le conteneur d’extrait de code||
|vs_logo_bk.gif|Utilisée pour les références de logo de contraste normal, tel que défini dans la balise de Branding.xml \<LogoFileName >.  Pour les produits Visual Studio, nom du logo est vs_logo_bk.gif.||
|vs_logo_wh.gif|Utilisée pour les références de logo haute normal, tel que défini dans la balise de Branding.xml \<LogoFileNameHC >.  Pour les produits Visual Studio, nom du logo est vs_logo_wh.gif.||
|ccOff.png|Graphique de sous-titrage||
|ccOn.png|Graphique de sous-titrage||
|ImageSprite.png|Utilisé pour restituer la zone réductible|développer ou réduire le graphique|

## <a name="deploy-a-set-of-topics"></a>Déployer un ensemble de rubriques

Il s’agit d’un didacticiel simple et rapide pour créer un jeu de déploiement de contenu de Help Viewer composé d’un fichier MSHA et l’ensemble des fichiers CAB ou MSHCs qui contient les rubriques. Le MSHA est un fichier XML qui décrit un ensemble de fichiers CAB ou les fichiers MSHC. La visionneuse d’aide peut lire le MSHA pour obtenir une liste de contenu (le fichier. CAB ou. Fichiers MSHC) disponibles pour l’installation locale.

Il s’agit uniquement une introduction décrivant le schéma XML très basique pour le MSHA visionneuse aide.  Voici un exemple d’implémentation sous cette vue d’ensemble et un exemple helpcontentsetup.msha.

Le nom de la MSHA, dans le cadre de ce manuel, est helpcontentsetup.msha (le nom du fichier peut être n’importe quoi, avec l’extension. MSHA). Helpcontentsetup.msha (exemple ci-dessous) doit contenir une liste des fichiers CAB ou MSHCs disponibles.  Le type de fichier doit être cohérent avec la MSHA (ne prend pas en charge une combinaison de types de fichiers MSHA et CAB). Pour chaque fichier CAB ou d’un MSHC, il doit y avoir un \<div classe = « package » >... \</div > (voir l’exemple ci-dessous).

Remarque : dans l’exemple d’implémentation ci-dessous, nous avons inclus le package de personnalisation. Il est essentiel d’inclure afin d’obtenir les éléments de rendu du contenu de Visual Studio nécessaires et les comportements de contenu.

Exemple de fichier helpcontentsetup.msha : (Remplacez « contenu set nom 1 » et « contenu jeu nom 2" etc. avec vos noms de fichiers.)

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

1. Créez un dossier local, quelque chose comme « C:\SampleContent »

2. Pour cet exemple, nous allons utiliser les fichiers MSHC pour contenir les rubriques.  Un MSHC est un fichier zip avec l’extension de fichier a été remplacée par .zip pour. MSHC.

3. Créer le ci-dessous helpcontentsetup.msha comme un fichier texte (le bloc-notes a été utilisé pour créer le fichier) et enregistrez-le dans le dossier indiqué ci-dessus (voir l’étape 1).

La classe « Branding » existe et est unique. La personnalisation mshc est inclus dans ce manuel afin que le contenu installé sera de personnalisation, et les comportements de contenu qui sont contenus dans les MSHCs aura les éléments de prise en charge appropriée contenus dans le package de personnalisation. Sans cela, les erreurs se produisent lorsque le système recherche les éléments de prise en charge qui ne font pas partie des extraits (installé) contenu.

Pour obtenir Visual Studio package de marque, copier le fichier Branding_en-US.mshc à C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ dans votre dossier de travail.

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

À l’aide et étendre les étapes ci-dessus permettent de VSP déployer leurs ensembles de contenu pour la visionneuse d’aide Visual Studio.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Ajouter une aide à Visual Studio Shell (intégré et isolé)

**Introduction**

Cette procédure pas à pas montre comment incorporer le contenu d’aide dans une application de Shell Visual Studio, puis le déployer.

**Spécifications**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 isolé Redist du Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Vue d’ensemble**

Le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell est une version de la [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE sur lequel vous pouvez baser une application. Ces applications contiennent le Shell isolé avec les extensions que vous créez. Utiliser des modèles de projet de Shell isolé, qui sont inclus dans le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Kit de développement logiciel, de générer des extensions.

Les étapes de base pour la création d’une application basée sur le Shell isolé et son aide :

1. Obtenir le [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] redistribuable du Shell ISO (un téléchargement de Microsoft).

2. Dans Visual Studio, créez une extension d’aide qui est basée sur le Shell isolé, par exemple, l’extension de l’aide de Contoso qui est décrite plus loin dans cette procédure pas à pas.

3. Encapsulez l’extension et l’interpréteur de commandes ISO redistribuables dans un déploiement MSI (une application le programme d’installation). Cette procédure pas à pas n’inclut pas d’une étape de configuration.

Créer un magasin de contenu Visual Studio. Pour le scénario de Shell intégré, remplacez Studio12 Visual le nom du catalogue produit comme suit :

- Créez le dossier C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Créez un fichier nommé CatalogType.xml et ajoutez-le au dossier. Le fichier doit contenir les lignes de code suivantes :

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Définir le magasin de contenu dans le Registre. Pour le Shell intégré, changez VisualStudio15 au nom de catalogue du produit :

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Clé : Valeur de chaîne de LocationPath : C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Clé : Valeur de chaîne de nom de catalogue : [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation

**Créer le projet**

Pour créer une extension de Shell isolé :

1. Dans Visual Studio, sous **fichier**, choisissez **nouveau projet**, sous **autres Types de projets** choisissez **extensibilité**, puis choisissez  **Shell isolé Visual Studio**. Nommez le projet `ContosoHelpShell`) pour créer un projet d’extensibilité basé sur le modèle de Shell isolé Visual Studio.

2. Dans l’Explorateur de solutions, dans le projet ContosoHelpShellUI, dans le dossier de fichiers de ressources, ouvrez ApplicationCommands.vsct. Assurez-vous que cette ligne est commentée (recherchez « No_Help ») : `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Appuyez sur la touche F5 pour compiler et exécuter **déboguer**. Dans l’instance expérimentale de l’IDE de Shell isolé, choisissez le **aide** menu. Assurez-vous que le **afficher l’aide**, **ajouter et supprimer le contenu d’aide**, et **définir les préférences pour aider à** commandes apparaissent.

4. Dans l’Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier de personnalisation de l’interpréteur de commandes, ouvrez ContosoHelpShell.pkgdef. Pour définir le catalogue d’aide de Contoso, ajoutez les lignes suivantes :

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Dans l’Explorateur de solutions, dans le projet ContosHelpShell, dans le dossier de personnalisation de l’interpréteur de commandes, ouvrez ContosoHelpShell.Application.pkgdef. Pour activer la touche F1, ajoutez les lignes suivantes :

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

6. Dans l’Explorateur de solutions, dans le menu contextuel de la solution ContosoHelpShell, choisissez le **propriétés** élément de menu. Sous **propriétés de Configuration**, sélectionnez **Configuration Manager**. Dans le **Configuration** colonne, modifier toutes les valeurs « Debug » sur « Release ».

7. Générez la solution. Cela crée un ensemble de fichiers dans un dossier de mise en production, qui sera utilisé dans la section suivante.

Pour effectuer ce test car si déployé :

1. Sur l’ordinateur que vous déployez Contoso pour installer l’interpréteur de commandes ISO (ci-dessus) téléchargé.

2. Créer un dossier dans \\\Program Files (x86)\\et nommez-le `Contoso`.

3. Copiez le contenu à partir du dossier de mise en production ContosoHelpShell à \\dossier de \Contoso\ \Program Files (x86).

4. Démarrez l’Éditeur du Registre en choisissant **exécuter** dans le **Démarrer** menu et en entrant `Regedit`. Dans l’Éditeur du Registre, choisissez **fichier**, puis **importation**. Recherchez le dossier de projet ContosoHelpShell. Dans le sous-dossier ContosoHelpShell, choisissez ContosoHelpShell.reg.

5. Créer un magasin de contenu :

    Pour l’interpréteur de commandes ISO - créer un magasin de contenu Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    Pour [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell intégré, créez le dossier C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Créer CatalogType.xml et l’ajouter au magasin de contenu (étape précédente) contenant :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Ajoutez les clés de Registre suivantes :

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valeur de chaîne de LocationPath :

    Pour l’interpréteur de commandes ISO :

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell intégré :

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Clé : Valeur de chaîne de nom de catalogue : [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation. Pour ISO Shell, ceci est le nom de votre catalogue.

8. Copier le contenu (fichiers CAB ou MSHC et MSHA) dans un dossier local.

9. Exemple de ligne de commande Shell intégré pour le test de magasin de contenu. Pour ISO Shell, modifiez les valeurs de catalogue et launchingApp comme il convient de faire correspondre le produit.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Lancez l’application Contoso (à partir de la racine de l’application Contoso). Au sein de l’interpréteur de commandes ISO, choisissez le **aide** élément de menu, puis remplacez le **définir les préférences pour aider à** à **utilisation de l’aide locale**.

11. Dans l’interpréteur de commandes, choisissez le **aide** élément de menu, puis **afficher l’aide**. La visionneuse d’aide locale doit lancer. Choisissez l’onglet **Gérer le contenu**. Sous **Source d’Installation**, choisissez le **disque** case d’option. Choisissez le **...**  bouton et accédez au dossier local contenant le contenu de Contoso (copié dans le dossier local dans l’étape ci-dessus). Choisissez le helpcontentsetup.msha. Contoso doit maintenant s’afficher sous forme de livre dans les sélections de livre. Choisissez **ajouter**, puis choisissez le **mise à jour** bouton (coin inférieur droit).

12. Dans l’IDE de Contoso, appuyez sur la touche F1 pour tester les fonctionnalités de la touche F1.

## <a name="additional-resources"></a>Ressources supplémentaires

Pour l’API de Runtime, consultez [API d’aide Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Pour plus d’informations sur la façon de tirer parti de l’API d’aide, consultez [exemples de code de visionneuse d’aide](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Vous pouvez envoyer des suggestions de fonctionnalités sur [Communauté de développeurs](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
