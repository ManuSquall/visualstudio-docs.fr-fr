---
title: Syntax Colorizing in a Legacy Language Service (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704710"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Couleurs de syntaxe dans un service de langage hérité
La colorisation syntaxe est une fonctionnalité qui provoque différents éléments d’un langage de programmation à être affichés dans un fichier source dans différentes couleurs et styles. Pour prendre en charge cette fonctionnalité, vous devez fournir un analyseur ou un scanner qui peut identifier les types d’éléments lexical ou de jetons dans le fichier. De nombreuses langues distinguent les mots clés, les délimitations (comme les parenthèses ou les accolades) et les commentent en les colorisant de différentes façons.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Extending the Editor and Language Services](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="implementation"></a>Implémentation
 Pour soutenir la colorisation, le cadre de <xref:Microsoft.VisualStudio.Package.Colorizer> paquet géré (MPF) comprend la classe, qui implémente l’interface. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Cette classe interagit avec un <xref:Microsoft.VisualStudio.Package.IScanner> pour déterminer le jeton et les couleurs. Pour plus d’informations sur les scanners, voir [Legacy Language Service Parser et Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer> classe marque ensuite chaque personnage du jeton avec les informations de couleur et renvoie cette information à l’éditeur affichant le fichier source.

 L’information couleur retournée à l’éditeur est un index dans une liste d’éléments colorables. Chaque élément colorable spécifie une valeur de couleur et un ensemble d’attributs de police, tels que gras ou strikethrough. L’éditeur fournit un ensemble d’éléments colorables par défaut que votre service linguistique peut utiliser. Tout ce que vous devez faire est de spécifier l’index de couleur approprié pour chaque type de jeton. Cependant, vous pouvez fournir un ensemble d’éléments colorables personnalisés et les indices que vous fournissez pour les jetons, et référencez votre propre liste d’éléments colorables au lieu de la liste par défaut. Vous devez également `RequestStockColors` définir l’entrée du registre `RequestStockColors` à 0 (ou ne pas spécifier l’entrée du tout) pour prendre en charge les couleurs personnalisées. Vous pouvez définir cette entrée de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> registre avec un paramètre désigné à l’attribut défini par l’utilisateur. Pour plus d’informations sur l’enregistrement d’un service linguistique et l’établissement de ses options, voir [Enregistrement d’un service de langue héritée](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Éléments coloriables personnalisés
 Pour fournir vos propres articles colorables <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> personnalisés, vous devez remplacer la méthode et <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> la méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. La première méthode renvoie le nombre d’articles colorables personnalisés que votre service linguistique prend en charge et le second obtient l’élément colorable personnalisé par index. Vous créez la liste par défaut d’objets colorables personnalisés. Dans le constructeur de votre service linguistique, tout ce que vous devez faire est de fournir chaque élément colorable avec un nom. Visual Studio gère automatiquement le boîtier où l’utilisateur sélectionne un ensemble différent d’éléments colorables. Ce nom est ce qui apparaît dans la page de propriété **Fonts and Colors** sur la boîte de dialogue **Options** (disponible à partir du menu Visual Studio **Tools)** et ce nom détermine quelle couleur un utilisateur a remplacé. Les choix de l’utilisateur sont stockés dans un cache dans le registre et accessibles par le nom de couleur. La page de propriété **Fonts and Colors** répertorie tous les noms de couleurs par ordre alphabétique, de sorte que vous pouvez regrouper vos couleurs personnalisées en précédant chaque nom de couleur avec votre nom de langue; par exemple, "**TestLanguage- Commentaire**" et "**TestLanguage- Mot-clé**". Ou vous pouvez regrouper vos éléments colorables par type, "**Commentaire (TestLanguage)**" et "**Mot-clé (TestLanguage)**". Le regroupement par nom de langue est préférable.

> [!CAUTION]
> Il est fortement recommandé que vous incluiez le nom de la langue dans le nom d’élément colorable pour éviter les collisions avec les noms d’objets colorables existants.

> [!NOTE]
> Si vous changez le nom d’une de vos couleurs pendant le développement, vous devez réinitialiser le cache que Visual Studio a créé la première fois que vos couleurs ont été consultées. Vous pouvez le faire en exécutant la commande **Reset the Experimental Hive** à partir du menu du programme Visual Studio SDK.

 Notez que le premier élément de votre liste d’éléments colorables n’est jamais référencé. Visual Studio fournit toujours les couleurs et les attributs de texte par défaut pour cet article. La façon la plus simple de traiter avec ceci est de fournir un article colorable de placeholder comme premier élément.

### <a name="high-color-colorable-items"></a>Articles colorables couleur haute couleur
 Les articles colorables peuvent également prendre en charge <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> des valeurs de couleur 24 ou élevées à travers l’interface. La classe <xref:Microsoft.VisualStudio.Package.ColorableItem> MPF <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> prend en charge l’interface et les couleurs 24 bits sont spécifiées dans le constructeur avec les couleurs normales. Pour plus d'informations, consultez la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. L’exemple ci-dessous montre comment définir les couleurs 24 bits pour les mots clés et les commentaires. Les couleurs 24 bits sont utilisées lorsque la couleur 24 bits est prise en charge sur le bureau de l’utilisateur; sinon, les couleurs normales de texte sont employées.

 Rappelez-vous, ce sont les couleurs par défaut pour votre langue; l’utilisateur peut changer ces couleurs à ce qu’ils veulent.

### <a name="example"></a>Exemple
 Cet exemple montre une façon de déclarer et de peupler un tableau d’articles colorables personnalisés en utilisant la <xref:Microsoft.VisualStudio.Package.ColorableItem> classe. Cet exemple définit le mot clé et les couleurs de commentaire en utilisant des couleurs 24 bits.

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

## <a name="the-colorizer-class-and-the-scanner"></a>La classe Colorizer et le Scanner
 La <xref:Microsoft.VisualStudio.Package.LanguageService> classe de <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> base a une <xref:Microsoft.VisualStudio.Package.Colorizer> méthode qui instantanéiantes la classe. Le scanner qui est <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> retourné de <xref:Microsoft.VisualStudio.Package.Colorizer> la méthode est passé au constructeur de classe.

 Vous devez <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implémenter la <xref:Microsoft.VisualStudio.Package.LanguageService> méthode dans votre propre version de la classe. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilise le scanner pour obtenir toutes les informations de couleur symbolique.

 Le scanner doit remplir <xref:Microsoft.VisualStudio.Package.TokenInfo> une structure pour chaque jeton qu’il trouve. Cette structure contient des informations telles que la travée que le jeton occupe, l’indice <xref:Microsoft.VisualStudio.Package.TokenTriggers>de couleur à utiliser, quel type est le jeton, et les déclencheurs symboliques (voir ). Seule la portée et l’index de <xref:Microsoft.VisualStudio.Package.Colorizer> couleur sont nécessaires pour la colorisation par la classe.

 L’indice de <xref:Microsoft.VisualStudio.Package.TokenInfo> couleur stocké dans la <xref:Microsoft.VisualStudio.Package.TokenColor> structure est généralement une valeur de l’énumération, qui fournit un certain nombre d’indices nommés correspondant à divers éléments linguistiques tels que les mots clés et les opérateurs. Si votre liste d’éléments colorables <xref:Microsoft.VisualStudio.Package.TokenColor> personnalisés correspond aux éléments présentés dans le recensement, alors vous pouvez simplement utiliser le recensement comme couleur pour chaque jeton. Toutefois, si vous avez des éléments colorables supplémentaires ou si vous ne voulez pas utiliser les valeurs existantes dans cet ordre, vous pouvez organiser votre liste d’éléments colorables personnalisés en fonction de vos besoins et retourner l’index approprié dans cette liste. Assurez-vous de jeter l’index à <xref:Microsoft.VisualStudio.Package.TokenColor> <xref:Microsoft.VisualStudio.Package.TokenInfo> un lors de son stockage dans la structure; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ne voit que l’index.

### <a name="example"></a>Exemple
 L’exemple suivant montre comment le scanner peut identifier trois types de jetons : nombres, ponctuation et identificateurs (tout ce qui n’est pas un nombre ou une ponctuation). Cet exemple est à des fins illustratives seulement et ne représente pas une mise en œuvre complète de l’analyse et du scanner. Il suppose qu’il `Lexer` ya `GetNextToken()` une classe avec une méthode qui retourne une chaîne.

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
