---
title: Coloration de la syntaxe dans un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19561363affada05154e15142bd32a30a5d051d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722830"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Couleurs de syntaxe dans un service de langage hérité
La colorisation de syntaxe est une fonctionnalité qui permet d’afficher différents éléments d’un langage de programmation dans un fichier source dans des couleurs et des styles différents. Pour prendre en charge cette fonctionnalité, vous devez fournir un analyseur ou un scanneur qui peut identifier les types d’éléments lexicaux ou de jetons dans le fichier. De nombreux langages distinguent les mots clés, les délimiteurs (tels que les parenthèses ou les accolades) et les commentaires en les colorisant de différentes façons.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [extension de l’éditeur et des services de langage](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="implementation"></a>Implémentation
 Pour prendre en charge la colorisation, Managed package Framework (MPF) comprend la classe <xref:Microsoft.VisualStudio.Package.Colorizer>, qui implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Cette classe interagit avec un <xref:Microsoft.VisualStudio.Package.IScanner> pour déterminer le jeton et les couleurs. Pour plus d’informations sur les scanneurs, consultez analyseur et analyseur [de service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La classe <xref:Microsoft.VisualStudio.Package.Colorizer> marque ensuite chaque caractère du jeton avec les informations de couleur et retourne ces informations à l’éditeur qui affiche le fichier source.

 Les informations de couleur retournées à l’éditeur sont un index dans une liste d’éléments coloriables. Chaque élément coloriable spécifie une valeur de couleur et un ensemble d’attributs de police, tels que le gras ou le barré. L’éditeur fournit un ensemble d’éléments colorables par défaut que votre service de langage peut utiliser. Il vous suffit de spécifier l’index de couleur approprié pour chaque type de jeton. Toutefois, vous pouvez fournir un ensemble d’éléments coloriables personnalisés et les index que vous fournissez pour les jetons, et faire référence à votre propre liste d’éléments coloriables à la place de la liste par défaut. Vous devez également affecter la valeur 0 à l’entrée de Registre `RequestStockColors` (ou ne pas spécifier l’entrée de `RequestStockColors`) pour prendre en charge les couleurs personnalisées. Vous pouvez définir cette entrée de Registre avec un paramètre nommé sur l’attribut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> défini par l’utilisateur. Pour plus d’informations sur l’inscription d’un service de langage et la définition de ses options, consultez [inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Éléments coloriables personnalisés
 Pour fournir vos propres éléments coloriables personnalisés, vous devez substituer la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> et <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> sur la classe <xref:Microsoft.VisualStudio.Package.LanguageService>. La première méthode retourne le nombre d’éléments coloriables personnalisés que votre service de langage prend en charge et le second obtient l’élément coloriable personnalisé par index. Vous créez la liste par défaut d’éléments coloriables personnalisés. Dans le constructeur de votre service de langage, il vous suffit de fournir chaque élément coloriable avec un nom. Visual Studio gère automatiquement le cas où l’utilisateur sélectionne un autre ensemble d’éléments coloriables. Ce nom apparaît dans la page de propriétés **polices et couleurs** de la boîte de dialogue **options** (accessible à partir du menu **Outils** de Visual Studio) et ce nom détermine la couleur qu’un utilisateur a remplacée. Les choix de l’utilisateur sont stockés dans un cache dans le registre et sont accessibles par le nom de couleur. La page de propriétés **polices et couleurs** répertorie tous les noms de couleurs par ordre alphabétique. vous pouvez ainsi regrouper vos couleurs personnalisées en faisant précéder chaque nom de couleur d’un nom de langue. par exemple, «**TestLanguage-comment**» et «**TestLanguage-Keyword**». Ou vous pouvez regrouper vos éléments coloriables par type, "**Comment (TestLanguage)** " et "**Keyword (TestLanguage)** ". Le regroupement par nom de langue est préféré.

> [!CAUTION]
> Il est fortement recommandé d’inclure le nom du langage dans le nom de l’élément coloriable pour éviter les collisions avec les noms d’éléments coloriables existants.

> [!NOTE]
> Si vous modifiez le nom de l’une de vos couleurs pendant le développement, vous devez réinitialiser le cache créé par Visual Studio la première fois que vous avez accédé à vos couleurs. Pour ce faire, vous pouvez exécuter la commande **Réinitialiser la ruche expérimentale** à partir du menu du programme SDK de Visual Studio.

 Notez que le premier élément de votre liste d’éléments coloriables n’est jamais référencé. Visual Studio fournit toujours les couleurs et les attributs de texte par défaut pour cet élément. Le moyen le plus simple de le gérer consiste à fournir un élément colorable d’espace réservé comme premier élément.

### <a name="high-color-colorable-items"></a>Éléments coloriables de couleur supérieure
 Les éléments coloriables peuvent également prendre en charge des valeurs de couleur 24 bits ou élevées par le biais de l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>. La classe MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> prend en charge l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> et les couleurs 24 bits sont spécifiées dans le constructeur avec les couleurs normales. Pour plus d'informations, consultez la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. L’exemple ci-dessous montre comment définir les couleurs 24 bits pour les mots clés et les commentaires. Les couleurs 24 bits sont utilisées quand les couleurs 24 bits sont prises en charge sur le Bureau de l’utilisateur. dans le cas contraire, les couleurs de texte normales sont utilisées.

 N’oubliez pas qu’il s’agit des couleurs par défaut de votre langue. l’utilisateur peut modifier ces couleurs en fonction de ce qu’elle veut.

### <a name="example"></a>Exemple
 Cet exemple montre une façon de déclarer et de remplir un tableau d’éléments coloriables personnalisés à l’aide de la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. Cet exemple définit les couleurs des mots clés et des commentaires à l’aide de couleurs 24 bits.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>La classe Coloriseur et le scanneur
 La classe de <xref:Microsoft.VisualStudio.Package.LanguageService> de base a une méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> qui instantiantes la classe <xref:Microsoft.VisualStudio.Package.Colorizer>. Le scanneur retourné par la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> est passé au constructeur de classe <xref:Microsoft.VisualStudio.Package.Colorizer>.

 Vous devez implémenter la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> dans votre propre version de la classe <xref:Microsoft.VisualStudio.Package.LanguageService>. La classe <xref:Microsoft.VisualStudio.Package.Colorizer> utilise le scanneur pour obtenir toutes les informations de couleur de jeton.

 Le scanneur doit remplir une structure <xref:Microsoft.VisualStudio.Package.TokenInfo> pour chaque jeton qu’il trouve. Cette structure contient des informations telles que l’étendue occupée par le jeton, l’index de couleur à utiliser, le type de jeton et les déclencheurs de jeton (voir <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Seul l’index d’étendue et de couleur est nécessaire pour la colorisation par la classe <xref:Microsoft.VisualStudio.Package.Colorizer>.

 L’index de couleur stocké dans la structure <xref:Microsoft.VisualStudio.Package.TokenInfo> est généralement une valeur de l’énumération <xref:Microsoft.VisualStudio.Package.TokenColor>, qui fournit un certain nombre d’index nommés correspondant à différents éléments de langage tels que les mots clés et les opérateurs. Si votre liste d’éléments coloriables personnalisés correspond aux éléments présentés dans l’énumération <xref:Microsoft.VisualStudio.Package.TokenColor>, vous pouvez simplement utiliser l’énumération comme couleur pour chaque jeton. Toutefois, si vous avez d’autres éléments coloriables ou si vous ne souhaitez pas utiliser les valeurs existantes dans cet ordre, vous pouvez organiser votre liste d’éléments coloriables personnalisés en fonction de vos besoins et retourner l’index approprié dans cette liste. Veillez simplement à effectuer un cast de l’index en <xref:Microsoft.VisualStudio.Package.TokenColor> lors de son stockage dans la structure de <xref:Microsoft.VisualStudio.Package.TokenInfo> ; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ne voit que l’index.

### <a name="example"></a>Exemple
 L’exemple suivant montre comment le scanneur peut identifier trois types de jetons : des nombres, des signes de ponctuation et des identificateurs (tout ce qui n’est pas un nombre ou une ponctuation). Cet exemple est fourni à titre d’illustration uniquement et ne représente pas une implémentation complète de l’analyseur et du scanneur. Il part du principe qu’il existe une classe `Lexer` avec une méthode `GetNextToken()` qui retourne une chaîne.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>Voir aussi
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)