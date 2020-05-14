---
title: Compilateur de couleurs VSIX ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703902"
---
# <a name="vsix-color-compiler"></a>Compilateur de couleur VSIX
L’outil Visual Studio Extension Color Compiler est une application de console qui prend un fichier .xml représentant les couleurs pour les thèmes existants Visual Studio et le secrètement à un fichier .pkgdef de sorte que ces couleurs peuvent être utilisées dans Visual Studio. Parce qu’il est facile de comparer les différences entre les fichiers .xml, cet outil est utile pour gérer les couleurs personnalisées dans le contrôle des sources. Il peut également être accroché dans des environnements de construction de sorte que la sortie de la construction est un fichier valide .pkgdef.

 **Schéma thème XML**

 Un fichier complet de thème .xml ressemble à ceci :

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Thème**

 Le \<thème>'élément définit un thème entier. Un thème doit contenir \<au moins une catégorie> élément. Les éléments thématiques sont définis comme ceci :

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Nom|[Requis] Le nom du thème|
|GUID|[Requis] GuiD du thème (doit correspondre au formatage GUID)|

 Lors de la création de couleurs personnalisées pour Visual Studio, ces couleurs doivent être définies pour les thèmes suivants. Si aucune couleur n’existe pour un thème particulier, Visual Studio tente de charger les couleurs manquantes du thème Lumière.

|||
|-|-|
|**Nom du thème**|**Thème GUID**|
|Léger|De3dbbcd-f642-433c-8353-8f1df4370aba|
|Foncé|1ded0138-47ce-435e-84ef-9ec1f439b749|
|Bleu|a4d6a176-b948-4b29-8c66-53c97a1ed7d0|
|Contraste élevé|a4d6a176-b948-4b29-8c66-53c97a1ed7d0|

 **Catégorie**

 L’élément \<> de catégorie définit une collection de couleurs dans un thème. Les noms de catégorie fournissent des regroupements logiques et doivent être définis aussi étroitement que possible. Une catégorie doit contenir \<au moins un élément> couleur. Les éléments de catégorie sont définis comme ceci :

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Nom|[Requis] Le nom de la catégorie|
|GUID|[Requis] GuiD de la catégorie (doit correspondre au formatage GUID)|

 **Color**

 L’élément \<Color> définit une couleur pour un composant ou un état d’interface utilisateur. Le système de nommage préféré pour une couleur est [type d’assurance-chômage] [État]. N’utilisez pas le mot «couleur», car il est redondant. Une couleur doit indiquer clairement le type d’élément et les situations, ou « état », pour lesquels la couleur sera appliquée. Une couleur ne doit pas être vide, et \<doit contenir l’un ou les deux d’un> de fond et \<au premier plan> élément. Les éléments de couleur sont définis comme ceci :

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Nom|[Requis] Le nom de la couleur|

 **Contexte et/ou premier plan**

 Les \<éléments de> \<et> de premier plan de fond définissent la valeur et le type d’une couleur pour l’arrière-plan ou le premier plan d’un élément d’interface utilisateur. Ces éléments n’ont pas d’enfants.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**Attribut**|**Définition**|
|Type|[Requis] Le type de la couleur. Les valeurs possibles sont les suivantes :<br /><br /> *CT_INVALID:* La couleur est invalide ou non définie.<br /><br /> *CT_RAW:* Une valeur BRUTE ARGB.<br /><br /> *CT_COLORINDEX:* NE PAS UTILISER.<br /><br /> *CT_SYSCOLOR:* Une couleur système Windows de SysColor.<br /><br /> *CT_VSCOLOR:* Une couleur Visual Studio de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* La couleur automatique.<br /><br /> *CT_TRACK_FOREGROUND:* NE PAS UTILISER.<br /><br /> *CT_TRACK_BACKGROUND:* NE PAS UTILISER.|
|Source|[Requis] La valeur de la couleur représentée dans l’hexadecimal|

 Toutes les valeurs soutenues par le __VSCOLORTYPE’énumération sont soutenues par le schéma de l’attribut Type. Cependant, nous vous recommandons d’utiliser seulement CT_RAW et CT_SYSCOLOR.

 **Tous ensemble**

 Il s’agit d’un exemple simple d’un thème valide .xml fichier:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil
 **Syntaxe**

 VsixColorCompiler \<XML fichier> \<fichier PkgDef> \<d’args en option>

 **Arguments**

||||
|-|-|-|
|**Nom de commutateur**|**Remarques**|**Requis ou facultatif**|
|Sans nom (.xml fichier)|C’est le premier paramètre anonyme et c’est le chemin vers le fichier XML à convertir.|Obligatoire|
|Sans nom (.pkgdef fichier)|Il s’agit du deuxième paramètre anonyme et est le chemin de sortie pour le fichier généré .pkgdef.<br /><br /> Défaut: \<XML Filename>.pkgdef|Facultatif|
|/noLogo|La configuration de ce drapeau empêche l’impression des informations sur les produits et le droit d’auteur.|Facultatif|
|/?|Imprimez des informations sur l’aide.|Facultatif|
|/help|Imprimez des informations sur l’aide.|Facultatif|

 **Exemples**

- VsixColorCompiler D: xml-colors.xml D:pkgdef-colors.pkgdef

- VsixColorCompiler D: xml-colors.xml /noLogo

## <a name="notes"></a>Notes

- Cet outil exige que la dernière version du temps d’exécution VCMD soit installée.

- Seuls les fichiers uniques sont pris en charge. La conversion en vrac via des chemins de dossier n’est pas prise en charge.

## <a name="sample-output"></a>Exemple de sortie
 Le fichier .pkgdef généré par l’outil sera similaire aux touches ci-dessous :

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
