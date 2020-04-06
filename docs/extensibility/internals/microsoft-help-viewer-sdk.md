---
title: Microsoft Aide Viewer SDK ( france) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707151"
---
# <a name="microsoft-help-viewer-sdk"></a>Kit SDK de Microsoft Help Viewer

Cet article contient les tâches suivantes pour visual Studio Help Viewer intégrateurs:

- Création d’un sujet (soutien F1)

- Création d’un package de marque de contenu Help Viewer

- Déploiement d’un ensemble d’articles

- Ajout d’aide à la coque Visual Studio (intégrée ou isolée)

- Ressources supplémentaires

## <a name="create-a-topic-f1-support"></a>Créer un sujet (support F1)

Cette section donne un aperçu des composantes d’un sujet présenté, des exigences de sujet, une courte description de la façon de créer un sujet (y compris les exigences de support F1) et enfin, un sujet d’exemple avec son résultat rendu.

**Aider le spectateur Aperçu du sujet**

Lorsqu’un sujet est appelé pour le rendu, le Visual d’aide obtient les éléments de paquet de marque qui sont associés au sujet au moment de l’installation ou de la dernière mise à jour, avec le sujet XHTML, et combine les deux pour aboutir à la vue de contenu présenté (données de marque et données de sujet).  Le paquet de marque contient des logos, un support pour les comportements de contenu et du texte de marque (copyright, etc.).  Voir "Créer le paquet de branding" ci-dessous pour plus d’informations sur les éléments du paquet de marque.  Dans le cas où il n’y a pas de paquet de marque associé au sujet, le Visual d’aide utilisera le paquet de marque de repli situé dans la racine d’application Help Viewer (Branding_en-US.mshc).

**Aidez les exigences du sujet du spectateur**

Pour être rendu correctement dans le Visualise d’aide, le contenu du sujet brut doit être W3C Basic 1.1 XHTML.

Un sujet contient généralement deux sections :

- Métadonnées (voir Référence des métadonnées de contenu) : données sur le sujet, par exemple, l’ID unique sur le sujet, la valeur des mots clés, le sujet TOC ID, ID de nœud parental, etc.

- Contenu corporel : conforme à W3C Basic 1.1 XHTML, qui comprend des comportements de contenu pris en charge (zone pliable, extrait de code, etc. Une liste complète est affichée ci-dessous).

Visual Studio Branding Package contrôles pris en charge:

- Liens

- CodeSnippet

- CollapsibleArea (en)

- Membre hérité

- LangueSpecificText

Chaînes linguistiques soutenues (non sensibles au cas) :

- javascript

- csharp ou c #

- cplusplus ou visualc OU c

- jscript

- visualbasic ou vb

- f' ou fsharp ou fs

- autre - une chaîne qui représente un nom de langue

**Création d’un sujet De visionneuse d’aide**

Créez un nouveau document XHTML nommé ContosoTopic4.htm, et incluez l’étiquette de titre (ci-dessous).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Ensuite, ajoutez des données pour définir comment le sujet doit être présenté (automarré ou non), comment référencer ce sujet pour la F1, où ce sujet existe au sein du TOC, son ID (pour référence de lien par d’autres sujets), etc. Voir le tableau "Content Metadata" ci-dessous pour une liste complète des métadonnées prises en charge.

- Dans ce cas, nous utiliserons notre propre package de marque, une variante du package de marque Visual Studio Help Viewer.

- Ajoutez le méta nom et la valeur F1 ("Microsoft.Help.F1" contenu " ContosoTopic4") qui correspondra à la valeur F1 fournie dans le sac de propriété IDE. (Voir la section Soutien F1 pour plus d’informations.) C’est la valeur qui est appariée à l’appel F1 de l’intérieur de l’IDE pour afficher ce sujet lorsque F1 est choisi dans l’IDE.

- Ajouter l’ID du sujet. C’est la chaîne qui est utilisée par d’autres sujets pour lier à ce sujet. C’est l’ID De visionneuse d’aide pour ce sujet.

- Pour le TOC, ajoutez le nœud parent de ce sujet pour définir où ce nœud TOC de sujet apparaîtra.

- Pour le TOC, ajoutez l’ordre de nœud de ce sujet. Lorsque le nœud parent a `n` un nombre de nœuds pour enfants, définissez dans l’ordre des nœuds d’enfant l’emplacement de ce sujet. Par exemple, ce sujet est le numéro 4 des 4 sujets pour enfants.

Exemple de métadonnées :

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

**L’organe thématique**

Le corps (sans compter l’en-tête et le pied) du sujet contiendra des liens de page, une section de note, une zone pliable, un extrait de code, et une section de texte spécifique à la langue.  Consultez la section de l’image de marque pour obtenir de l’information sur les domaines du sujet présenté.

1. Ajouter une étiquette de titre de sujet:`<div class="title">Contoso Topic 4</div>`

2. Ajouter une section de note :`<div class="alert"> add your table tag and text </div>`

3. Ajouter une zone pliable :`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Ajouter un extrait de code :`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Ajoutez du texte spécifique `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` à `devLangnu=` la langue de code : Note qui vous permet d’entrer d’autres langues. Par exemple, `devLangnu="Fortran"` affiche Fortran lorsque le code extrait DisplayLanguage - Fortran

6. Ajouter des liens de page :`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Remarque : pour la nouvelle coloration de code «Display Language» (exemple, F, Cobol, Fortran) dans l’extrait de code sera monochrome.

**Exemple Aider le sujet du spectateur** Le code illustre comment définir les métadonnées, un extrait de code, une zone pliable et un texte spécifique à la langue.

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

**Soutien F1**

Dans Visual Studio, la sélection de F1 génère des valeurs fournies à partir du placement du curseur dans l’IDE et remplit un « sac de propriété » avec les valeurs fournies (en fonction de l’emplacement du curseur. Lorsque le curseur est plus de fonctionnalité x, fonctionnalité x est actif / dans la mise au point et remplit sac de propriété avec des valeurs.  Lorsque F1 est sélectionné le sac de propriété est peuplé et Visual Studio F1 code cherche à voir si les clients par défaut Source d’aide est locale ou en ligne (en ligne est la valeur par défaut), puis crée la chaîne appropriée en fonction du paramètre des utilisateurs (en ligne est la valeur par défaut) - shell exécuter (voir le Guide d’administrateur d’aide pour les paramètres de lancement exe) avec des paramètres pour le spectateur d’aide locale - mot-clé (s) du sac de propriété si l’aide locale est la valeur par défaut , ou l’URL MSDN avec le mot clé dans la liste des paramètres.

Si trois cordes sont retournées pour la F1, appelée chaîne multi-valeur, prenez le premier terme, cherchez un succès, et si elle est trouvée, nous avons terminé; sinon, passez à la chaîne suivante.  L’ordre compte. La présentation des mots clés multi-valeurs doit être la plus longue chaîne à la chaîne la plus courte.  Pour vérifier cela dans le cas des mots clés multi-valeurs, regardez la chaîne d’URL F1 en ligne, qui inclura le mot clé choisi.

Dans Visual Studio 2012, nous avons intentionnellement fait un fossé plus fort entre en ligne et hors ligne, de sorte que si le paramètre de l’utilisateur était pour en ligne, alors nous avons simplement passé la demande de F1 directement à notre service de requête en ligne sur MSDN plutôt que de router à travers l’agent de bibliothèque d’aide que nous avions dans Visual Studio 2010. Nous nous appuyons ensuite sur un état de « contenu fournisseur installé et vrai » pour déterminer s’il faut faire quelque chose de différent dans ce contexte. Si c’est vrai, nous effectuons alors cette logique d’analyse et de routage en fonction de ce que vous souhaitez prendre en charge pour vos clients. Si faux, alors nous allons juste à MSDN. Si le paramètre de l’utilisateur est à local, alors tous les appels vont au moteur d’aide local.

Diagramme de flux F1:

![Flux F1](../../extensibility/internals/media/f1flow.png "F1flow (F1flow)")

Lorsque la source de contenu aide par défaut help Viewer est configuré en ligne (Lancement dans le navigateur) :

- Visual Studio Partner (VSP) caractéristiques émettent une valeur pour le sac de propriété F1 (sac de propriété prefix.keyword et URL en ligne pour le préfixe trouvé dans le registre): F1 envoie un PARAmètre VSP URL SUR le navigateur.

- Visual Studio (éditeur de langue, éléments de menu spécifiques Visual Studio, etc.) : F1 envoie une URL Visual Studio au navigateur.

Lorsque la source de contenu d’aide par défaut du Visual Help est définie à l’aide locale (Launch in Help Viewer) :

- VSP caractéristiques où le lien entre le sac de propriété F1 et l’indice local de magasin (c’est-à-dire, le sac de propriété prefix.keyword - la valeur trouvée dans l’index du magasin local): F1 rend le sujet dans le Visual d’aide.

- Caractéristiques Visual Studio (pas la possibilité pour le VSP de remplacer le sac de propriété émis par les fonctionnalités Visual Studio): F1 rend un sujet Visual Studio dans le Visual Viewer.

Définissez les valeurs de registre suivantes pour activer F1 Fallback pour le contenu d’aide au fournisseur. F1 Fallback signifie que le Visualiseur d’aide est configuré pour rechercher le contenu F1 Aide en ligne, et le contenu du fournisseur est installé localement sur le disque dur des utilisateurs. Le Visualiseur d’aide devrait regarder l’aide locale pour le contenu, même si le paramètre par défaut est pour l’aide en ligne.

1. Définissez la valeur **VendorContent** sous la clé du registre Help 2.3 :

   - Pour les systèmes d’exploitation 32 bits :

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"dword:00000001

   - Pour les systèmes d’exploitation 64 bits :

        HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3-Catalogs-VisualStudio15

        "VendorContent"dword:00000001

2. Enregistrez l’espace nom du partenaire sous la clé du registre Help 2.3 :

   - Pour les systèmes d’exploitation 32 bits :

      HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Help-v2.3-Partner<em> \\<namespace\></em>

      "emplacement" "hors ligne"

   - Pour les systèmes d’exploitation 64 bits :

      HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3-Partner<<em> \\ namespace\></em>

      "emplacement" "hors ligne"

**Base Native Namespace Parsing**

Pour activer l’analyse de l’espace nom natif de base, dans le registre ajouter un nouveau DWORD par le nom de: BaseNativeNamespaces et définir sa valeur à 1 (sous la clé du catalogue qu’ils veulent prendre en charge).  Par exemple, si vous souhaitez utiliser le catalogue Visual Studio, vous pouvez ajouter la clé du chemin :

HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3-Catalogs-VisualStudio15

Lorsqu’un mot clé F1 dans le format HEADER/METHOD est rencontré, le caractère '/' sera analysé, ce qui entraîne la construction suivante :

- HEADER: sera l’espace de nom qui peut être utilisé pour s’inscrire dans le registre

- MÉTHODE: cela deviendra le mot clé qui passe à travers.

Par exemple, étant donné une bibliothèque personnalisée appelée CustomLibrary et une méthode appelée MyTestMethod, quand une demande de F1 arrive, il sera formaté comme `CustomLibrary/MyTestMethod`.

Un utilisateur peut alors enregistrer CustomLibrary comme l’espace nom sous la ruche Partenaires, et fournir n’importe quelle clé de localisation qu’ils désirent, et le mot clé passé à la requête sera MyTestMethod.

**Activez l’outil de débogage d’aide dans l’IDE**

Ajouter la clé et la valeur du registre suivant :

::: moniker range="vs-2017"

**HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-15.0 -Aide dynamique**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-16.0 -Aide dynamique**

::: moniker-end

Valeur: Afficher la sortie de débbug dans les données de détail: OUI

Dans l’IDE, sous l’élément menu Aide, sélectionnez **Debug Help Context**.

**Métadonnées de contenu**

Dans le tableau suivant, toute chaîne qui apparaît entre les parenthèses est un lieu qui doit être remplacé par une valeur reconnue. Par exemple, \<dans meta name "Microsoft.Help.Local" contenu "[code de langue]" />, "[code linguistique]" doit être remplacé par une valeur telle que "en-nous".

| Propriété (REPRÉSENTATION HTML) | Description |
| - | - |
| \<meta name "Microsoft.Help.Local" content "[code linguistique]" /> | Définit un lieu pour ce sujet. Si cette balise est utilisée dans un sujet, elle doit être utilisée une seule fois et elle doit être insérée au-dessus de toutes les autres balises Microsoft Help. Si cette balise n’est pas utilisée, le texte du corps du sujet est indexé à l’aide de disjoncteur qui est associé au local du produit, si elle est spécifiée; sinon, le disjoncteur de mot en-nous est utilisé. Cette étiquette est conforme à l’ISOC RFC 4646. Pour vous assurer que Microsoft Help fonctionne correctement, utilisez cette propriété au lieu de l’attribut langue générale. |
| \<meta name"Microsoft.Help.TopicLocale" content "[code de langue]" /> | Définit un endroit pour ce sujet lorsque d’autres lieux sont également utilisés. Si cette balise est utilisée dans un sujet, elle doit être utilisée une seule fois. Utilisez cette balise lorsque le catalogue contient du contenu dans plus d’une langue. Plusieurs sujets d’un catalogue peuvent avoir le même ID, mais chacun doit spécifier un TopicLocale unique. Le sujet qui spécifie un TopicLocale qui correspond à la localisation du catalogue est le sujet qui est affiché dans le tableau des contenus. Cependant, toutes les versions linguistiques du sujet sont affichées dans les résultats de recherche. |
| \<titre>[Titre]\</titre> | Spécifie le titre de ce sujet. Cette balise est nécessaire, et doit être utilisé une seule fois dans un sujet. Si le corps du sujet ne \<contient pas de div titre> section, ce titre est affiché dans le sujet et dans le tableau du contenu. |
| \<meta name"" Microsoft.Help.Keywords" content "[aKeywordPhrase]"/> | Spécifie le texte d’un lien qui est affiché dans le volet index du Visualise d’aide. Lorsque le lien est cliqué, le sujet s’affiche. Vous pouvez spécifier plusieurs mots clés d’index pour un sujet, ou vous pouvez omettre cette balise si vous ne voulez pas que des liens vers ce sujet apparaissent dans l’index. Les mots clés "K" des versions antérieures de Help peuvent être convertis à cette propriété. |
| \<méta name"Microsoft.Help.Id" contenu "[TopicID]"/> | Définit l’identifiant pour ce sujet. Cette balise est nécessaire, et doit être utilisé une seule fois dans un sujet. L’ID doit être unique parmi les sujets du catalogue qui ont le même cadre local. Dans un autre sujet, vous pouvez créer un lien vers ce sujet en utilisant cette pièce d’identité. |
| \<méta name"Microsoft.Help.F1" content "[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Spécifie le mot clé F1 pour ce sujet. Vous pouvez spécifier plusieurs mots clés F1 pour un sujet, ou vous pouvez omettre cette balise si vous ne souhaitez pas que ce sujet soit affiché lorsqu’un utilisateur d’application presse F1. Typiquement, un seul mot clé F1 est spécifié pour un sujet. Les mots clés "F" des versions antérieures de Help peuvent être convertis à cette propriété. |
| \<méta nameMD "Description" contenu "[description du sujet]" /> | Fournit un bref résumé du contenu dans ce sujet. Si cette balise est utilisée dans un sujet, elle doit être utilisée une seule fois. Cette propriété est accessible directement par la bibliothèque de requêtes; il n’est pas stocké dans le fichier index. |
| méta name"Microsoft.Help.TocParent" content "[parent_Id]"/> | Spécifie le sujet parent de ce sujet dans le tableau des contenus. Cette balise est nécessaire, et doit être utilisé une seule fois dans un sujet. La valeur est la Microsoft.Help.Id du parent. Un sujet peut avoir un seul emplacement dans le tableau du contenu. "-1" est considéré comme le sujet ID pour la racine TOC. Dans [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], cette page est La page d’accueil De Help Viewer. C’est la même raison pour laquelle nous ajoutons spécifiquement TocParent-1 à certains sujets pour nous assurer qu’ils apparaissent au plus haut niveau. La page d’accueil Help Viewer est une page système et donc non remplaçable. Si un VSP essaie d’ajouter une page avec un ID de -1, il peut être ajouté à l’ensemble de contenu, mais Help Viewer sera toujours utiliser la page du système - Aider Viewer Home |
| \<méta name"Microsoft.Help.TocOrder" content "[integer positif]"/> | Précise où dans le tableau des contenus ce sujet apparaît par rapport à ses sujets pairs. Cette balise est nécessaire, et doit être utilisé une seule fois dans un sujet. La valeur est un entier. Un sujet qui spécifie un intégrer de moindre valeur apparaît au-dessus d’un sujet qui spécifie un intégrer de plus grande valeur. |
| \<méta name"Microsoft.Help.Product" content "[code produit]"/> | Spécifie le produit que ce sujet décrit. Si cette balise est utilisée dans un sujet, elle doit être utilisée une seule fois. Ces informations peuvent également être fournies comme un paramètre qui est transmis à l’indexeur d’aide. |
| \<méta name"Microsoft.Help.ProductVersion" contenu "[numéro de version]"/> | Spécifie la version du produit que ce sujet décrit. Si cette balise est utilisée dans un sujet, elle doit être utilisée une seule fois. Ces informations peuvent également être fournies comme un paramètre qui est transmis à l’indexeur d’aide. |
| \<méta name"Microsoft.Help.Category" content "[string]"/> | Utilisé par les produits pour identifier les sous-sections de contenu. Vous pouvez identifier plusieurs sous-sections pour un sujet, ou vous pouvez omettre cette balise si vous ne voulez pas de liens pour identifier des sous-sections. Cette balise est utilisée pour stocker les attributs de TargetOS et TargetFrameworkMoniker lorsqu’un sujet est converti à partir d’une version antérieure de Help. Le format du contenu est AttributeName:AttributeValue. |
| \<méta name"Microsoft.Help.TopicVersion content "[numéro de version thématique]"/> | Spécifie cette version du sujet lorsque plusieurs versions existent dans un catalogue. Parce que Microsoft.Help.Id n’est pas garanti d’être unique, cette balise est nécessaire lorsque plus d’une version d’un sujet existe dans un catalogue, par exemple, quand un catalogue contient un sujet pour le cadre .NET 3.5 et un sujet pour le cadre .NET 4 et les deux ont la même Microsoft.Help.Id. |
| \<méta name "SelfBranded" content "[TRUE or FALSE]"/> | Précise si ce sujet utilise le package de marque start-up Help Library Manager ou un ensemble de branding spécifique au sujet. Cette balise doit être soit VRAI, soit FALSE. Si c’est VRAI, alors le paquet de marque pour le sujet associé remplace le paquet de marque qui est défini lorsque Help Library Manager commence de sorte que le sujet est rendu comme prévu, même si elle diffère du rendu d’autres contenus. S’il s’agit de FALSE, le sujet actuel est rendu selon le paquet d’image de marque qui est défini lorsque Help Library Manager commence. Par défaut, Help Library Manager suppose que l’auto-image de marque est fausse à moins que la variable SelfBranded ne soit déclarée VRAIE; par conséquent, vous n’avez pas à déclarer \<le méta nom "SelfBranded" contenu "FALSE"/>. |

## <a name="create-a-branding-package"></a>Créer un package d’image de marque

La version Visual Studio comprend un certain nombre de différents produits Visual Studio, y compris les coquilles isolated et intégrées pour Visual Studio Partners.  Chacun de ces produits nécessite un certain degré de support de marque de contenu d’aide basé sur le sujet, unique au produit.  Par exemple, les sujets Visual Studio doivent avoir une présentation cohérente de marque, tandis que SQL Studio, qui enveloppe ISO Shell, nécessite sa propre marque de contenu d’aide unique pour chaque sujet.  Un partenaire Shell intégré peut vouloir que ses sujets d’aide soient dans le contenu parent du produit Visual Studio Aide tout en maintenant leur propre image de marque de sujet.

Des emballages de marque sont installés par le produit contenant le Visualise d’aide.  Pour les produits Visual Studio :

- Un package de marque de repli (Branding_\<local>.mshc) est installé dans la racine de l’application Help Viewer 2.3 (exemple : Fichiers de programme C :x86) -Microsoft Help ViewerMD v2.3) par le pack de langue Help Viewer.  Ceci est utilisé pour les cas où soit le paquet de marque de produit n’est pas installé (aucun contenu n’a été installé) ou où le paquet de marque installé est corrompu.  Les éléments Visual Studio (logo et Feedback) sont ignorés lorsque le paquet de marque de repli de l’application est utilisé.

- Lorsque le contenu Visual Studio est installé à partir du service de paquet de contenu, un package d’image de marque est également installé (pour la première fois scénario d’installation de contenu).  S’il y a une mise à jour du paquet de marque, la mise à jour est installée lorsque la prochaine mise à jour de contenu ou l’action d’installation de paquet supplémentaire se produit.

Le Microsoft Help Viewer prend en charge l’image de marque de sujets basés sur les métadonnées thématiques.

- Lorsque les métadonnées de sujet définit l’auto-marque - vrai, rendre le sujet tel quel, ne rien faire (dans la mesure où l’image de marque).

- Lorsque les métadonnées thématiques définissent la marque auto-marquée - faux, utilisez le paquet de marque associé à la valeur des métadonnées TopicVendor.

- Lorsque les métadonnées thématiques définissent le nom "Microsoft.Help.TopicVendor" nom de paquet de marque "\< dans le fournisseur MSHA>, utilisez le package de marque défini dans la valeur de contenu.

- Dans le catalogue Visual Studio, il existe une application prioritaire des paquets de branding.  La première image de marque par défaut visual Studio est appliquée, puis, si elle est définie dans les métadonnées thématiques et prise en charge par le package de marque associé (tel que défini dans l’installation msha), l’image de marque définie par le fournisseur est appliquée comme un remplacement.

Les éléments de marque se divisent généralement en trois catégories principales :

- Éléments d’en-tête (exemples incluent le lien de rétroaction, le texte conditionnel de renonciation, le logo)

- Comportements de contenu (exemples incluent des éléments de texte de contrôle d’expansion/effondrement et des éléments d’extrait de code)

- Éléments de footer (exemple Droit d’auteur)

Les éléments considérés comme des éléments de marque comprennent (détaillés dans cette spécification) :

- Logo catalogue/produit (exemple, Visual Studio)

- Lien de rétroaction et éléments de courrier électronique

- Texte de non-responsabilité

- Texte du droit d’auteur

Les fichiers de soutien dans le package d’image de marque Visual Studio Help Viewer comprennent :

- Graphiques (logos, icônes, etc.)

- Branding.js - fichiers scripts supportant les comportements de contenu

- Branding.xml - chaînes qui sont régulièrement utilisées sur le contenu du catalogue.  Note: pour Visual Studio localisation des éléments texte dans le branding.xml, inclure _locID "\<valeur unique>"

- Branding.css - définitions de style pour la cohérence de présentation

- Printing.css - définitions de style pour une présentation imprimée cohérente

Comme indiqué ci-dessus, les paquets de branding sont associés au sujet :

- Lorsque SelfBranded - faux est défini dans les métadonnées, le sujet hérite du paquet de marque catalogue

- Ou lorsque SelfBranded - faux et il ya un paquet de branding unique défini dans le MSHA et disponible lorsque le contenu est installé

Pour les VSP implémentant des paquets d’image de marque personnalisés (contenu VSP, SelfBranded-True), une façon de procéder est de commencer par le paquet de marque de repli (installé avec le Visualise d’aide), et de changer le nom du fichier, le cas échéant.  Le fichier\<local Branding_>.mshc est un fichier zip avec l’extension du fichier changé en .mshc, donc il suffit de changer l’extension de .mshc à .zip et extraire le contenu.  Voir ci-dessous pour les éléments de l’emballage de marque et de modifier le cas échéant (par exemple, changer le logo pour le logo VSP et la référence au logo dans le fichier Branding.xml, mise à jour Branding.xml par VSP spécifiques, etc.).

Lorsque toutes les modifications sont effectuées, créez un fichier zip contenant les éléments de marque souhaités et modifiez l’extension en .mshc.

Pour associer le package d’image de marque personnalisé, créez le MSHA, qui contient la référence au fichier mshc de marque avec le mshc de contenu (contenant les sujets).  Voir ci-dessous "MSHA" pour savoir comment créer un MSHA de base.

Le fichier Branding.xml contient une liste d’éléments utilisés pour rendre \<systématiquement des éléments spécifiques dans un sujet lorsque le sujet contient méta name "Microsoft.Help.SelfBranded" contenu "faux" />.  La liste Visual Studio des éléments du fichier Branding.xml est listée ci-dessous.  Cette liste est destinée à être utilisée comme modèle pour les adoptants d’ISO Shell, où ils modifient ces éléments (par exemple le logo, la rétroaction et le droit d’auteur) pour répondre à leurs propres besoins d’image de marque de produit.

Remarque : les variables notées par les « n » ont des dépendances au code - la suppression ou la modification de ces valeurs entraînera des erreurs et peut-être un plantage d’applications. Les identificateurs de localisation (exemple _locID"codesnippet.n") sont inclus dans le package de marque Visual Studio.

**Branding.xml (en anglais)**

| | |
| - | - |
| Fonctionnalités : | **CollapsibleArea (en)** |
| Utilisez : | Élargir s’effondre le texte de contrôle du contenu |
| **Élément** | **Valeur** |
| ExpandText | Développez |
| CollapseText (en) | Réduire |
| Fonctionnalités : | **CodeSnippet** |
| Utilisez : | Texte de contrôle d’extrait de code.  Remarque : Le contenu de l’extrait de code avec l’espace « Non-Breaking » sera changé en espace. |
| **Élément** | **Valeur** |
| CopyToClipboard (en anglais) | Copier dans le Presse-papiers |
| AfficherColorizedText | Afficher Coloriized |
| CombinedVBTabDisplayLanguage | Base visuelle (échantillon) |
| VBDéclaration | Déclaration |
| VBUsage (VBUsage) | Usage |
| Fonctionnalités : | **Commentaires, Footer et Logo** |
| Utilisez : | Fournir un contrôle de rétroaction pour le client pour fournir des commentaires sur le sujet actuel par e-mail.  Texte de droit d’auteur pour le contenu.  Définition du logo. |
| **Élément** | **Valeur (Ces chaînes peuvent être modifiées pour répondre aux besoins d’adoption de contenu.)** |
| Copyright | © 2013 Microsoft Corporation. Tous droits réservés. |
| SendFeedback (en) | \<a href{0}" {1} ">Envoyer\<des commentaires /un> sur ce sujet à Microsoft. |
| FeedbackLink (en) | |
| LogoTitle LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Fonctionnalités : | **Avertissement** |
| Utilisez : | Un ensemble de clauses de non-responsabilité spécifiques aux cas pour le contenu traduit par la machine. |
| **Élément** | **Valeur** |
| MT_Editable | Cet article a été traduit à la machine. Si vous avez une connexion Internet, sélectionnez «Voir ce sujet en ligne» pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_NonEditable | Cet article a été traduit à la machine. Si vous avez une connexion Internet, sélectionnez «Voir ce sujet en ligne» pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_QualityEditable | Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez «Voir ce sujet en ligne» pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_QualityNonEditable | Cet article a été traduit manuellement. Si vous avez une connexion Internet, sélectionnez «Voir ce sujet en ligne» pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_BetaContents | Cet article a été traduit à la machine pour une version préliminaire. Si vous avez une connexion Internet, sélectionnez «Voir ce sujet en ligne» pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| MT_BetaRecycledContents | Cet article a été traduit manuellement pour une version préliminaire. Si vous avez une connexion Internet, sélectionnez «Voir ce sujet en ligne» pour afficher cette page en mode modifiable avec le contenu original en anglais en même temps. |
| Fonctionnalités : | **LienTable** |
| Utilisez : | Soutien aux liens de sujet en ligne |
| **Élément** | **Valeur** |
| LinkTableTitle (en) | Tableau de lien |
| TopicEnuLinkText | Voir la\<version anglaise /un> de ce sujet qui est disponible sur votre ordinateur. |
| TopicOnlineLinkText | Voir ce \<sujet un{0}href " {1}>\<en ligne /un> |
| OnlineText (en ligne) | En ligne |
| Fonctionnalités : | **Contrôle audio vidéo** |
| Utilisez : | Afficher les éléments et le texte pour le contenu vidéo |
| **Élément** | **Valeur** |
| MultiMediaNotSupported | Internet Explorer 9 ou plus {0} doit être installé pour prendre en charge le contenu. |
| Vidéotex | affichage de la vidéo |
| AudioTexte | streaming audio |
| OnlineVideoLinkText (en ligneVideoLinkText) | \<p>Pour visionner la vidéo associée {0} \<à ce sujet, cliquez sur {2}\<un href ">{1}ici /un>. \</p> |
| OnlineAudioLinkText | \<p>Pour écouter l’audio associé à {0} \<ce sujet,{1}cliquez sur un {2}\<href ">ici /un>. \</p> |
| Fonctionnalités : | **Contenu Non Installé de contrôle** |
| Utilisez : | Éléments de texte (cordes) utilisés pour le rendu de contentnotinstalled.htm |
| **Élément** | **Valeur** |
| ContentNotInstalledTitle | Aucun contenu n’a été trouvé sur votre ordinateur. |
| ContentNotInstalledDownloadContentText | \<p>Pour télécharger du contenu \<sur votre ordinateur, un href "{0}>{1} cliquez sur l’onglet\<Gérer /un>. \</p> |
| ContenuNotintaltexte | \<p>Aucun contenu n’est installé sur votre ordinateur. Consultez votre administrateur pour l’installation locale de contenu d’aide. \</p> |
| Fonctionnalités : | **Sujet non trouvé le contrôle** |
| Utilisez : | Éléments de texte (cordes) utilisés pour le rendu de topicnotfound.htm |
| **Élément** | **Valeur** |
| SujetNotFoundTitle | Impossible de trouver le sujet demandé sur votre ordinateur. |
| TopicNotFoundViewOnlineText | \<p>Le sujet que vous avez demandé n’a \<pas été{0}trouvé {1} sur votre ordinateur,\<mais vous pouvez un href " ">voir le sujet en ligne / un>. \</p> |
| TopicNotFoundDownloadContentText | \<p>Voir le volet de navigation pour \<les liens vers{0} {1} des sujets similaires, ou\<un href ">cliquez sur l’onglet Gérer /un> pour télécharger du contenu sur votre ordinateur. \</p> |
| SujetNotFoundText | \<p>Le sujet que vous avez demandé n’a pas été trouvé sur votre ordinateur. \</p> |
| Fonctionnalités : | **Sujet Contrôle corrompu** |
| Utilisez : | Éléments de texte (cordes) utilisés pour le rendu de topiccorrupted.htm |
| **Élément** | **Valeur** |
| SujetCorruptedTitle | Impossible d’afficher le sujet demandé. |
| SujetCorruptedViewOnlineText | \<p>Help Viewer n’est pas en mesure d’afficher le sujet demandé. Il peut y avoir une erreur dans le contenu du sujet ou une dépendance du système sous-jacent. \</p> |
| Fonctionnalités : | **Contrôle de la page d’accueil** |
| Utilisez : | Texte supportant l’affichage du contenu de nœud de haut niveau Help Viewer. |
| **Élément** | **Valeur** |
| HomePageTitle | Aide Viewer Home |
| Page d’accueilIntroduction | \<p>Bienvenue au Visualise d’aide Microsoft, une source essentielle d’informations pour tous ceux qui utilisent des outils, des produits, des technologies et des services Microsoft. Le Visual d’aide vous donne accès à des informations de référence et de référence, à des exemples de code, à des articles techniques, et plus encore. Pour trouver le contenu dont vous avez besoin, parcourez la table de contenu, utilisez la recherche en texte intégral ou naviguez à travers le contenu à l’aide de l’index des mots clés. \</p> |
| AccueilContentInstallText | \<p>\<br />Utilisez le \<href "{0} {1} ">Gérer\<le contenu /un onglet> pour\<faire ce \<qui suit: ul>li>Ajouter du contenu à votre ordinateur. \</li>\<li>Vérifiez les mises à jour de votre contenu local. \</li>\<li>Retirez le contenu de votre ordinateur. \</li>\</ul>\</p> |
| AccueilPageInstalledBooks | Livres installés |
| AccueilNoBooksInstalled | Aucun contenu n’a été trouvé sur votre ordinateur. |
| AccueilPageHelpSettings | Paramètres de contenu d’aide |
| AccueilPageHelpSettingsText | \<p>Votre réglage actuel est d’aide locale. Le Visual d’aide affiche le contenu que vous avez installé sur votre ordinateur. \<br />Pour modifier votre source de contenu d’aide, \<sur la{0}barre de menu Visual Studio, choisissez le style de portée " ">Help, Set Help Preference\</span>. \<br />\</p> |
| Mégaoctet | Mo |

**branding.js**

Le fichier branding.js contient JavaScript utilisé par les éléments de marque Visual Studio Help Viewer.  Voici une liste des éléments de marque et de la fonction JavaScript de soutien.  Toutes les chaînes à localisées pour ce fichier sont définies dans la section "Localizable Strings" en haut de ce fichier.  Le fichier ICL a été créé pour les chaînes de loc dans le fichier branding.js.

||||
|-|-|-|
|**Caractéristiques de marque**|**Fonction JavaScript**|**Description**|
|Var...||Définir des variables|
|Obtenez la langue de code utilisateur|setUserPreferenceLang|cartographier un index à la langue de code|
|Définir et obtenir des valeurs de cookie|getCookie, setCookie||
|Membre hérité|changeMembersLabel|Élargir /effondrement membre hérité|
|Quand SelfBranded-False|Onload|Lisez la chaîne de requête pour vérifier s’il s’agit d’une demande d’impression.  Réglez tous les codesnippets pour concentrer l’onglet préféré de l’utilisateur.  S’il s’agit d’une demande d’impression, puis l’ensemble estPrinterFriendly à vrai. Vérifiez s’il y a un mode de contraste élevé.|
|Code Extrait|addSpecificTextLanguageTagSet||
||getIndexDeDevLang||
||ChangeTab (en)||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard (en anglais)||
|CollapsibleArea (en)|addToCollapsibleControlSet|écrire tout l’objet de contrôle pliable dans la liste.|
||CA_Click|basé sur l’état de la zone pliable, définit quelle image et texte à présenter|
|Soutien contrasté pour Logo|isBlackBackground ()|Appelé pour déterminer si l’arrière-plan est noir.  Seulement précis lorsqu’il est en mode contraste élevé.|
||isHighContrast ()|utiliser une travée colorée pour détecter le mode contraste élevé|
||onHighContrast (noir)|Appelé lorsque le contraste élevé est détecté|
|Fonctionnalité LST|||
||addToLanSpecTextIdSet(id)||
||updateLST (currentLang)||
||getDevLangDeCodeSnippet (lang)||
|Fonctionnalités MultiMedia|Légende (début, fin, texte, style)||
||findAllMediaControls (normaliséId)||
||getActivePlayer (normaliséId)||
||LégendesOnOff(id)||
||àSeconds(t)||
||getAllComments (nœud)||
||styleRectify (styleName, styleValue)||
||showCC (id)||
||sous-titre(id)||

**FICHIERS HTM**

Le paquet d’image de marque contient un ensemble de fichiers HTM qui prennent en charge les scénarios de communication d’informations clés pour aider les utilisateurs de contenu, par exemple une page d’accueil qui contient une section décrivant les ensembles de contenu sont installés et les pages indiquant à l’utilisateur quand les sujets ne peuvent pas être trouvés dans l’ensemble local de sujets. Ces fichiers HTM peuvent être modifiés par produit.  Les fournisseurs d’ISO Shell sont en mesure de prendre le paquet de marque par défaut et de modifier le comportement et le contenu de ces pages pour adapter leurs besoins.  Ces fichiers se réfèrent à leur package d’image de marque respectif afin que les balises de marque pour obtenir le contenu correspondant à partir du fichier branding.xml.

||||
|-|-|-|
|**File**|**Utilisation**|**Source de contenu affichée**|
|page d’accueil.htm|Il s’agit d’une page qui affiche le contenu actuellement installé, et tout autre message approprié à présenter à l’utilisateur au sujet de leur contenu.  Ce fichier a l’attribut de méta données supplémentaires "Microsoft.Help.Id" contenu "-1" qui place ce contenu en haut du contenu local TOC.||
||META_HOME_PAGE_TITLE_ADD </>|Branding.xml, \<tag HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, \<tag HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<tag HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Section de direction Branding.xml tag\<HomePageInstalledBooks>, les \<données générées à partir de l’application, HomePageNoBooksInstalled> quand aucun livre n’est installé.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Section de direction Branding.xml tag \<HomePageHelpSettings \<>, section texte HomePageHelpSettingsText>.|
|topiccorrupted.htm|Quand un sujet existe dans l’ensemble local, mais pour une raison quelconque ne peut pas être affiché (contenu corrompu).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<tag TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, \<tag TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Lorsqu’un sujet ne se trouve pas dans l’ensemble de contenu local, ni disponible en ligne||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<tag TopicNotFoundTitle>|
||META_TOPIC_NOT_FOUND_ID_ADD </>|Branding.xml, \<tag TopicNotFoundViewOnlineText> \<- TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, \<tag TopicNotFoundText>|
|contentnotinstalled.htm|Lorsqu’il n’y a pas de contenu local installé pour le produit.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, \<tag ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, \<tag ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, \<tag ContentNotInstalledText>|

**Fichiers CSS**

Le visual Studio Help Viewer Branding Package contient deux fichiers css pour soutenir la présentation cohérente du contenu Visual Studio Help :

- Branding.css - contient des éléments css pour le rendu où SelfBranded-faux

- Printer.css - contient des éléments css pour le rendu où SelfBranded-faux

Les fichiers Branding.css comprennent des définitions pour la présentation du sujet Visual Studio (la\<mise en garde est que le branding.css contenu dans le local Branding_>.mshc du service de paquets peut changer).

**Fichiers graphiques**

Le contenu Visual Studio affiche un logo Visual Studio ainsi que d’autres graphiques.  La liste complète des fichiers graphiques dans le paquet de marque Visual Studio Help Viewer est affichée ci-dessous.

||||
|-|-|-|
|**File**|**Utilisation**|**Exemples**|
|clear.gif (en)|Utilisé pour rendre Collapsible Area||
|footer_slice.gif|Présentation de pied||
|info_icon.gif|Utilisé lors de l’affichage des informations|Clause d'exclusion de responsabilité|
|online_icon.gif|Cette icône doit être associée à des liens en ligne||
|tabLeftBD.gif|Utilisé pour rendre le conteneur d’extrait de code||
|tabRightBD.gif|Utilisé pour rendre le conteneur d’extrait de code||
|vs_logo_bk.gif|Utilisé pour les références de logo de contraste \<normale telles que définies dans Branding.xml tag LogoFileName>.  Pour les produits Visual Studio, le nom du logo est vs_logo_bk.gif.||
|vs_logo_wh.gif|Utilisé pour les références normales logo élevé \<tel que défini dans Branding.xml tag LogoFileNameHC>.  Pour les produits Visual Studio, le nom du logo est vs_logo_wh.gif.||
|ccOff.png (en)|Sous-titrage graphique||
|ccOn.png (en)|Sous-titrage graphique||
|ImageSprite.png|Utilisé pour rendre Collapsible Area|graphique élargi ou effondrement|

## <a name="deploy-a-set-of-topics"></a>Déployer un ensemble de sujets

Il s’agit d’un tutoriel simple et rapide pour créer un ensemble de déploiement de contenu Help Viewer composé d’un fichier MSHA et l’ensemble de cabines ou MSHCs contenant les sujets. Le MSHA est un fichier XML qui décrit un ensemble de taxis ou de fichiers MSHC. Le Visualiseur d’aide peut lire le MSHA pour obtenir une liste de contenu (le . CAB ou . Fichiers MSHC) disponibles pour l’installation locale.

Ce n’est qu’une amorce décrivant le schéma XML très basique pour le Visionnement d’aide MSHA.  Il y a un exemple d’implémentation ci-dessous ce bref aperçu et l’échantillon HelpContentSetup.msha.

Le nom de la MSHA, aux fins de cette amorce, est HelpContentSetup.msha (le nom du fichier peut être n’importe quoi, avec l’extension . MSHA). HelpContentSetup.msha (exemple ci-dessous) devrait contenir une liste des cabines ou des MSHC disponibles.  Le type de fichier doit être uniforme au sein de la MSHA (ne prend pas en charge une combinaison de types de fichiers MSHA et CAB). Pour chaque CAB ou MSHC, \<il devrait y avoir une classe de div "paquet">... \</div> (voir l’exemple ci-dessous).

Remarque : dans l’exemple de mise en œuvre ci-dessous, nous avons inclus le paquet de marque. Ceci est essentiel à inclure afin d’obtenir le contenu Visual Studio nécessaire de rendu des éléments et des comportements de contenu.

Exemple de fichier HelpContentSetup.msha : (Remplacer le « nom de contenu 1 » et le « nom de contenu 2 » etc. avec vos noms de fichiers.)

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

1. Créez un dossier local, quelque chose comme «C: 'SampleContent"

2. Pour cet exemple, nous utiliserons les fichiers DU MSHC pour contenir les sujets.  Un MSHC est une fermeture éclair avec l’extension de fichier changé de .zip à . MSHC.

3. Créez le fichier helpContentSetup.msha ci-dessous sous forme de fichier texte (notepad a été utilisé pour créer le fichier) et enregistrez-le dans le dossier mentionné ci-dessus (voir étape 1).

La classe "Branding" existe et est unique. Le mshc de marque est inclus dans cette amorce de sorte que le contenu installé aura l’image de marque, et les comportements de contenu qui sont contenus dans les MSHC auront les éléments de support appropriés contenus dans le paquet de marque. Sans cela, des erreurs se traduiront lorsque le système recherche des éléments de support qui ne font pas partie du contenu déchiré (installé).

Pour obtenir le package de marque Visual Studio, copiez Branding_en-US.mshc fichier à C: 'Program Files (x86)-Microsoft Help Viewer’v2.3 ' à votre dossier de travail.

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

L’utilisation et l’extension des étapes ci-dessus permettront aux VSP de déployer leurs ensembles de contenu pour le Visual Studio Help Viewer.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Ajouter de l’aide à la Visual Studio Shell (Integrated and Isolated)

**Introduction**

Cette procédure pas à pas démontre comment intégrer le contenu Help dans une application Visual Studio Shell, puis le déployer.

**Configuration requise**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Isolated Shell Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Vue d’ensemble**

La [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell est une [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] version de l’IDE sur laquelle vous pouvez baser une application. Ces applications contiennent la coquille isolée ainsi que les extensions que vous créez. Utilisez des modèles de projets Isolated [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell, qui sont inclus dans le SDK, pour construire des extensions.

Les étapes de base pour créer une application shell isolée et son aide :

1. Obtenir [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] l’ISO Shell redistribuable (un téléchargement Microsoft).

2. Dans Visual Studio, créez une extension d’aide qui est basée sur la coquille isolée, par exemple, l’extension Contoso Help qui est décrite plus tard dans cette procédure pas à pas.

3. Enveloppez l’extension et l’ISO Shell redistribuable dans un MSI de déploiement (une configuration d’application). Cette procédure pas à pas n’inclut pas une étape d’installation.

Créez un magasin de contenu Visual Studio. Pour le scénario Integrated Shell, modifiez Visual Studio12 au nom du catalogue de produits comme suit :

- Créez le dossier C : 'ProgramData’Microsoft’HelpLibrary2'Catalogs-VisualStudio15.

- Créez un fichier nommé CatalogType.xml et ajoutez-le au dossier. Le fichier doit contenir les lignes de code suivantes :

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Définissez le magasin de contenu dans le registre. Pour la coque intégrée, changez VisualStudio15 au nom du catalogue de produits :

- HKLM-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3'Catalogs-VisualStudio15

   Clé: LocationPath Valeur de la chaîne: C: 'ProgramData’Microsoft’HelpLibrary2'Catalogs’VisualStudio15

- HKLM-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3'Catalogs-VisualStudio15-en-US

   Clé: CatalogName Valeur [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] de la chaîne: Documentation

**Créer le projet**

Pour créer une extension De Shell isolée :

1. Dans Visual Studio, sous **Fichier**, choisissez **New Project**, sous **d’autres types de projet** choisir **Extensibility**, puis choisir **Visual Studio Shell Isolated**. Nommez `ContosoHelpShell`le projet ) pour créer un projet d’extéabilité basé sur le modèle Visual Studio Isolated Shell.

2. Dans Solution Explorer, dans le projet ContosoHelpShellUI, dans le dossier Resource Files, ouvert ApplicationCommands.vsct. Assurez-vous que cette ligne est commentée (recherche de «No_Help») :`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Choisissez la clé F5 pour compiler et exécuter **Debug**. Dans le cas expérimental de l’IDE Coquille Isolée, choisissez le menu **Aide.** Assurez-vous que **l’aide De vue,** **ajouter et supprimer le contenu d’aide,** et définir les commandes **de préférence d’aide** apparaissent.

4. Dans Solution Explorer, dans le projet ContosHelpShell, dans le dossier Shell Customization, ouvert ContosoHelpShell.pkgdef. Pour définir le catalogue Contoso Help, ajoutez les lignes suivantes :

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Dans Solution Explorer, dans le projet ContosHelpShell, dans le dossier Shell Customization, ouvert ContosoHelpShell.Application.pkgdef. Pour activer F1 Aide, ajoutez les lignes suivantes :

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

6. Dans Solution Explorer, sur le menu contextuelle de la solution ContosoHelpShell, choisissez l’élément menu **Propriétés.** Sous **Configuration Properties**, sélectionnez Configuration **Manager**. Dans la colonne **Configuration,** modifiez chaque valeur "Debug" en "Release".

7. Générez la solution. Cela crée un ensemble de fichiers dans un dossier de version, qui sera utilisé dans la section suivante.

Pour tester cela comme s’il était déployé :

1. Sur la machine que vous déployez Contoso, installez le shell ISO téléchargé (d’en haut).

2. Créez un dossier \\dans les fichiers de\\programme (x86) et nommez-le `Contoso`.

3. Copiez le contenu du dossier de sortie ContosoHelpShell à \\l’adresse «Program Files) à «ContosoMD».

4. Démarrez l’éditeur de registre en `Regedit`choisissant **Run** in the **Start** menu et en entrant . Dans l’éditeur de registre, choisissez **Fichier**, puis **Import**. Naviguez vers le dossier du projet ContosoHelpShell. Dans le sous-plieur ContosoHelpShell, choisissez ContosoHelpShell.reg.

5. Créer un magasin de contenu :

    Pour ISO Shell - créez un magasin de contenu Contoso C: 'ProgramData’Microsoft’HelpLibrary2'Catalogs-ContosoDev12

    Pour [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] La coque intégrée, créez le dossier C : 'ProgramData’Microsoft’HelpLibrary2'Catalogs-VisualStudio15

6. Créez CatalogType.xml et ajoutez au magasin de contenu (étape précédente) contenant :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Ajoutez les clés de registre suivantes :

    HKLM-SOFTWARE-Wow6432Node-Microsoft-Help-v2.3'Catalogs-VisualStudio15Key: LocationPath Valeur de chaîne:

    Pour ISO Shell :

    c.R.: ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell intégrée :

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Clé: CatalogName Valeur [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] de chaîne: Documentation. Pour ISO Shell, c’est le nom de votre catalogue.

8. Copiez votre contenu (cabines ou MSHC et MSHA) à un dossier local.

9. Exemple Ligne de commande Shell intégrée pour le stockage de contenu de test. Pour ISO Shell, modifiez le catalogue et lancez les valeurs App, le cas échéant, pour correspondre au produit.

     "C:-Program Files (x86)-Microsoft Help Viewer-v2.3-HlpViewer.exe" /catalogName VisualStudio15/helpQuery method"page&id-ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Lancez l’application Contoso (à partir de la racine de l’application Contoso). Au sein d’ISO Shell, choisissez l’élément du menu **d’aide** et modifiez la **préférence d’aide** pour **utiliser l’aide locale.**

11. Dans la coquille, choisissez l’élément du menu **d’aide,** puis **consultez l’aide**. Le visualiseur d’aide local devrait lancer. Choisissez l’onglet Gérer le **contenu.** Sous **Source d’installation**, choisissez le bouton **d’option Disque.** Choisissez le bouton **...** et naviguez vers le dossier local contenant du contenu Contoso (copié sur le dossier local dans l’étape ci-dessus). Choisissez helpContentSetup.msha. Contoso devrait maintenant apparaître comme un livre dans les sélections de livres. Choisissez **Ajouter,** puis choisissez le bouton **Mise à jour** (coin inférieur droit).

12. Au sein de l’IDE Contoso, choisissez la clé F1 pour tester la fonctionnalité F1.

## <a name="additional-resources"></a>Ressources supplémentaires

Pour l’API Runtime, voir [Windows Help API](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Pour plus d’informations sur la façon de tirer parti de l’API Help, voir [les exemples de code Help Viewer](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Vous pouvez soumettre des suggestions de fonctionnalités sur [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
