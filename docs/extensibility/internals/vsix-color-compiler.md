---
title: "Compilateur de couleur VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Compilateur de couleur VSIX
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L’outil de compilateur de couleur Visual Studio Extension est une application console qui utilise un fichier .xml qui représente les couleurs des thèmes Visual Studio existants et les convertit en un .pkgdef de fichiers afin que ces couleurs peuvent être utilisées dans Visual Studio. Car il est facile de comparer les différences entre les fichiers .xml, cet outil est utile pour la gestion des couleurs personnalisées dans un contrôle de code source. Il également peut être raccordé à des environnements de build afin que la sortie de la génération est un fichier .pkgdef valide.  
  
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
  
 Le \< thème> élément définit un thème entier. Un thème doive contenir au moins un \< catégorie> élément. Éléments de thème sont définies comme suit :  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Nom|[Obligatoire] Le nom du thème|  
|GUID|[Obligatoire] GUID du thème (doit correspondre au GUID de mise en forme)|  
  
 Lorsque vous créez des couleurs personnalisées pour Visual Studio, ces couleurs doivent être définies pour les thèmes suivants. Si aucune couleur n’existe pour un thème particulier, Visual Studio tente de charger les couleurs manquantes dans le thème clair.  
  
|||  
|-|-|  
|**Nom de thème**|**GUID de thème**|  
|Clair|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Sombre|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Bleu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contraste élevé|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Catégorie**  
  
 Le \< catégorie> élément définit une collection de couleurs d’un thème. Les noms de catégorie fournissent des regroupements logiques et doivent être définis comme précisément que possible. Une catégorie doit contenir au moins un \< couleur> élément. Éléments de catégorie sont définies comme suit :  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Nom|[Obligatoire] Le nom de la catégorie|  
|GUID|[Obligatoire] GUID de la catégorie (doit correspondre au GUID de mise en forme)|  
  
 **Couleur**  
  
 Le \< couleur> élément définit une couleur d’un composant ou d’un état de l’interface Utilisateur. Le schéma d’affectation de noms par défaut pour une couleur est [type d’interface Utilisateur] [État]. N’utilisez pas le mot « color », car il est redondant. Une couleur doit clairement indiquer le type d’élément et les situations ou « état », pour laquelle la couleur s’applique. Une couleur ne doit pas être vide et doit comporter une ou deux un \< arrière-plan> et \< premier plan> élément. Éléments de couleur sont définies comme suit :  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Nom|[Obligatoire] Le nom de la couleur|  
  
 **Arrière-plan ou premier plan**  
  
 Le \< arrière-plan> et \< premier plan> éléments définissent la valeur d’une couleur et le type de l’arrière-plan ou premier plan d’un élément d’interface Utilisateur. Ces éléments ont pas d’enfants.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Type|[Obligatoire] Le type de la couleur. Il peut avoir l'une des valeurs suivantes :<br /><br /> *CT_INVALID :* la couleur est non valide ou non définie.<br /><br /> *CT_RAW :* une valeur ARGB brute.<br /><br /> *CT_COLORINDEX :* N’UTILISEZ PAS.<br /><br /> *CT_SYSCOLOR :* une couleur système Windows SysColor.<br /><br /> *CT_VSCOLOR :* une couleur Visual Studio à partir de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC :* la couleur automatique.<br /><br /> *CT_TRACK_FOREGROUND :* N’UTILISEZ PAS.<br /><br /> *CT_TRACK_BACKGROUND :* N’UTILISEZ PAS.|  
|Source|[Obligatoire] La valeur de couleur représentée au format hexadécimal|  
  
 Toutes les valeurs prises en charge par l’énumération __VSCOLORTYPE sont pris en charge par le schéma dans l’attribut de Type. Toutefois, nous vous recommandons d’utiliser uniquement CT_RAW et CT_SYSCOLOR.  
  
 **Assemblage**  
  
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
  
## <a name="how-to-use-the-tool"></a>L’utilisation de l’outil  
 **Syntaxe**  
  
 VsixColorCompiler \< fichier XML> \< PkgDef fichier> \< arguments facultatifs>  
  
 **Arguments**  
  
||||  
|-|-|-|  
|**Nom du commutateur**|**Notes de publication**|**Obligatoire ou facultatif**|  
|Sans nom (fichier .xml)|Ceci est le premier paramètre sans nom et le chemin d’accès au fichier XML à convertir.|Obligatoire|  
|Sans nom (fichier .pkgdef)|Ceci est le deuxième paramètre sans nom et le chemin de sortie pour le fichier .pkgdef généré.<br /><br /> Par défaut : \< nom du fichier XML>.pkgdef|Facultatif|  
|/noLogo|Définition de cet indicateur, les informations de copyright et de produit de l’impression s’arrête.|Facultatif|  
|/?|Imprimer des informations d’aide.|Facultatif|  
|/help|Imprimer des informations d’aide.|Facultatif|  
  
 **Exemples**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   /NoLogo de VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Notes  
  
-   Cet outil nécessite que la dernière version du runtime VC ++ soit installé.  
  
-   Seuls les fichiers uniques sont pris en charge. Conversion en bloc via les chemins d’accès n’est pas pris en charge.  
  
## <a name="sample-output"></a>Résultat de l'exemple  
 Le fichier .pkgdef généré par l’outil sera similaire à le ci-dessous clés :  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```