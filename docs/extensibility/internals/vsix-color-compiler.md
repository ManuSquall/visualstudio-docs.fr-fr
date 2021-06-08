---
title: Compilateur de couleur VSIX | Microsoft Docs
description: Découvrez l’outil de compilateur couleur de l’extension Visual Studio, qui est une application console qui remplace les couleurs des thèmes Visual Studio par un fichier. pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92914703ea4b293ac054c841251b37886bbc1d5a
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588460"
---
# <a name="vsix-color-compiler"></a>Compilateur de couleur VSIX
L’outil de compilateur couleur de l’extension Visual Studio est une application console qui prend un fichier .xml représentant les couleurs des thèmes Visual Studio existants et le remplace par un fichier. pkgdef afin que ces couleurs puissent être utilisées dans Visual Studio. Étant donné qu’il est facile de comparer les différences entre les fichiers .xml, cet outil est utile pour gérer les couleurs personnalisées dans le contrôle de code source. Il peut également être raccordé à des environnements de génération afin que la sortie de la génération soit un fichier. pkgdef valide.

 **Schéma XML de thème**

 Un fichier de .xml de thème complet se présente comme suit :

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

 L' \<Theme> élément définit un thème entier. Un thème doit contenir au moins un \<Category> élément. Les éléments de thème sont définis comme suit :

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Attribut**|**Définition**|
|-|-|
|Nom|Souhaitée Nom du thème|
|GUID|Souhaitée GUID du thème (doit correspondre à la mise en forme du GUID)|

 Lors de la création de couleurs personnalisées pour Visual Studio, ces couleurs doivent être définies pour les thèmes suivants. S’il n’existe aucune couleur pour un thème particulier, Visual Studio tente de charger les couleurs manquantes à partir du thème clair.

|**Nom du thème**|**GUID du thème**|
|-|-|
|Clair|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Sombre|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Bleu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Contraste élevé|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Catégorie**

 L' \<Category> élément définit une collection de couleurs dans un thème. Les noms de catégorie fournissent des regroupements logiques et doivent être définis de la manière la plus étroite possible. Une catégorie doit contenir au moins un \<Color> élément. Les éléments category sont définis comme suit :

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Attribut**|**Définition**|
|-|-|
|Nom|Souhaitée Nom de la catégorie|
|GUID|Souhaitée GUID de la catégorie (doit correspondre à la mise en forme du GUID)|

 **Couleur**

 L' \<Color> élément définit une couleur pour un composant ou un état d’interface utilisateur. Le schéma d’affectation de noms préféré pour une couleur est [type d’interface utilisateur] [État]. N’utilisez pas le mot « Color », car il est redondant. Une couleur doit indiquer clairement le type d’élément et les situations, ou « État », pour lesquelles la couleur sera appliquée. Une couleur ne doit pas être vide et doit contenir l’un des éléments ou les \<Background> deux \<Foreground> . Les éléments de couleur sont définis comme suit :

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Attribut**|**Définition**|
|-|-|
|Nom|Souhaitée Nom de la couleur|

 **Arrière-plan et/ou premier plan**

 Les \<Background> \<Foreground> éléments et définissent la valeur et le type d’une couleur pour l’arrière-plan ou le premier plan d’un élément d’interface utilisateur. Ces éléments n’ont pas d’enfants.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Attribut**|**Définition**|
|-|-|
|Type|Souhaitée Type de la couleur. Les valeurs possibles sont les suivantes :<br /><br /> *CT_INVALID :* La couleur n’est pas valide ou n’est pas définie.<br /><br /> *CT_RAW :* Valeur ARVB brute.<br /><br /> *CT_COLORINDEX :* N’UTILISEZ PAS.<br /><br /> *CT_SYSCOLOR :* Couleur système Windows à partir de SysColor.<br /><br /> *CT_VSCOLOR :* Couleur Visual Studio de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC :* Couleur automatique.<br /><br /> *CT_TRACK_FOREGROUND :* N’UTILISEZ PAS.<br /><br /> *CT_TRACK_BACKGROUND :* N’UTILISEZ PAS.|
|Source|Souhaitée Valeur de la couleur représentée au format hexadécimal|

 Toutes les valeurs prises en charge par l’énumération __VSCOLORTYPE sont prises en charge par le schéma dans l’attribut type. Toutefois, nous vous recommandons d’utiliser uniquement CT_RAW et CT_SYSCOLOR.

 **Ensemble**

 Voici un exemple simple de fichier de .xml de thème valide :

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

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Arguments**

|**Nom du commutateur**|**Remarques**|**Obligatoire ou facultatif**|
|-|-|-|
|Sans nom (fichier .xml)|Il s’agit du premier paramètre sans nom. il s’agit du chemin d’accès au fichier XML à convertir.|Obligatoire|
|Sans nom (fichier. pkgdef)|Il s’agit du deuxième paramètre sans nom et est le chemin de sortie du fichier. pkgdef généré.<br /><br /> Valeur par défaut : \<XML Filename> . pkgdef|Facultatif|
|/noLogo|La définition de cet indicateur arrête l’impression du produit et des informations de copyright.|Facultatif|
|/?|Imprimer les informations d’aide.|Facultatif|
|/help|Imprimer les informations d’aide.|Facultatif|

 **Exemples**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>Notes

- Cet outil requiert l’installation de la dernière version du runtime VC + +.

- Seuls les fichiers uniques sont pris en charge. La conversion en bloc via des chemins de dossiers n’est pas prise en charge.

- L’outil se trouve dans `<VS Install Path>\VSSDK\VisualStudioIntegration\Tools\Bin\`

## <a name="sample-output"></a>Exemple de sortie
 Le fichier. pkgdef généré par l’outil est semblable aux clés ci-dessous :

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
