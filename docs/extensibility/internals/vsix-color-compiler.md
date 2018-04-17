---
title: Compilateur de couleurs VSIX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-color-compiler"></a>Compilateur de couleurs VSIX
L’outil compilateur de couleur Visual Studio Extension est une application console qui accepte un fichier .xml qui représente les couleurs des thèmes Visual Studio existants et que les membres à un .pkgdef de fichiers afin que ces couleurs peuvent être utilisées dans Visual Studio. Comme il est facile de comparer les différences entre les fichiers .xml, cet outil est utile pour la gestion des couleurs personnalisées dans le contrôle de code source. Il également peut être raccordé environnements de build afin que la sortie de la build est un fichier .pkgdef valide.  
  
 **Schéma XML de thème**  
  
 Un fichier .xml de thème complète ressemble à ceci :  
  
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
  
 Le \<thème > élément définit un thème entier. Un thème doit contenir au moins un \<catégorie > élément. Éléments de thème sont définies comme suit :  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Name|[Obligatoire] Le nom du thème|  
|GUID|[Obligatoire] GUID du thème (doit correspondre au GUID de mise en forme)|  
  
 Lorsque vous créez des couleurs personnalisées pour Visual Studio, ces couleurs doivent être définies pour les thèmes suivants. Si aucune couleur n’existe pour un thème particulier, Visual Studio tente de charger les couleurs de manquants à partir de ce thème clair.  
  
|||  
|-|-|  
|**Nom de thème**|**GUID de thème**|  
|Clair|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Sombre|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Bleu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contraste élevé|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Catégorie**  
  
 Le \<catégorie > élément définit une collection de couleurs dans un thème. Noms de catégorie fournissent des regroupements logiques et doivent être définies comme précisément que possible. Une catégorie doit contenir au moins un \<couleur > élément. Éléments de catégorie sont définis comme suit :  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Name|[Obligatoire] Le nom de la catégorie|  
|GUID|[Obligatoire] GUID de catégorie (doit correspondre au GUID de mise en forme)|  
  
 **Couleur**  
  
 Le \<couleur > élément définit une couleur d’un composant ou d’un état de l’interface utilisateur. Le schéma d’affectation de noms par défaut pour une couleur est [type d’interface utilisateur] [État]. N’utilisez pas le mot « couleur », car elle est redondante. Une couleur doit clairement indiquer le type d’élément et les situations ou « état », pour laquelle la couleur s’applique. Une couleur ne doit pas être vide et doit contenir une ou les deux un \<arrière-plan > et \<au premier plan > élément. Éléments de couleur sont définies comme suit :  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Name|[Obligatoire] Le nom de la couleur|  
  
 **Arrière-plan et/ou de premier plan**  
  
 Le \<arrière-plan > et \<au premier plan > éléments définissent la valeur d’une couleur et le type de l’arrière-plan ou du premier plan de l’élément d’interface utilisateur. Ces éléments ont pas d’enfants.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Type|[Obligatoire] Le type de la couleur. Il peut avoir l'une des valeurs suivantes :<br /><br /> *CT_INVALID :* la couleur est non valide ou non définie.<br /><br /> *CT_RAW :* une valeur ARVB brute.<br /><br /> *CT_COLORINDEX :* N’UTILISEZ PAS.<br /><br /> *CT_SYSCOLOR :* une couleur système Windows SysColor.<br /><br /> *CT_VSCOLOR :* une couleur de Visual Studio à partir de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC :* la couleur automatique.<br /><br /> *CT_TRACK_FOREGROUND :* N’UTILISEZ PAS.<br /><br /> *CT_TRACK_BACKGROUND :* N’UTILISEZ PAS.|  
|Source|[Obligatoire] La valeur de la couleur représentée en notation hexadécimale|  
  
 Toutes les valeurs prises en charge par l’énumération __VSCOLORTYPE sont pris en charge par le schéma dans l’attribut de Type. Toutefois, nous vous recommandons d’utiliser uniquement CT_RAW et CT_SYSCOLOR.  
  
 **L’ensemble de**  
  
 Il s’agit d’un exemple simple d’un fichier .xml de thème valide :  
  
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
  
 VsixColorCompiler \<fichier XML > \<fichier PkgDef > \<arguments facultatifs >  
  
 **Arguments**  
  
||||  
|-|-|-|  
|**Nom du commutateur**|**Notes**|**Obligatoire ou facultatif**|  
|Sans nom (fichier .xml)|Ceci est le premier paramètre sans nom et le chemin d’accès au fichier XML à convertir.|Obligatoire|  
|Sans nom (fichier .pkgdef)|Ceci est le deuxième paramètre sans nom et le chemin de sortie pour le fichier .pkgdef généré.<br /><br /> Valeur par défaut : \<nom du fichier XML > .pkgdef|Facultatif|  
|/noLogo|Définition de cet indicateur arrête les informations de copyright et de produit à partir de l’impression.|Facultatif|  
|/?|Imprimer les informations d’aide.|Facultatif|  
|/help|Imprimer les informations d’aide.|Facultatif|  
  
 **Exemples**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   /NoLogo de VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Notes  
  
-   Cet outil nécessite que la version la plus récente du runtime VC ++ être installé.  
  
-   Seuls les fichiers uniques sont pris en charge. La conversion en bloc via les chemins d’accès de dossier n’est pas pris en charge.  
  
## <a name="sample-output"></a>Résultat de l'exemple  
 Le fichier .pkgdef généré par l’outil sera semblable à la ci-dessous clés :  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```