---
title: "Coloration de syntaxe dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b9d98323b3957108746b22702306c9155b142fb9
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Coloration de syntaxe dans un Service de langage hérité
Colorisation de la syntaxe est une fonctionnalité qui provoque des différents éléments d’un langage de programmation à afficher dans un fichier source dans différentes couleurs et styles. Pour prendre en charge cette fonctionnalité, vous devez fournir un analyseur ou l’analyseur qui peut identifier les types d’éléments lexicaux ou les jetons dans le fichier. De nombreux langages distinguent les mots clés, les délimiteurs (tels que des parenthèses ou d’accolades) et les commentaires en les colorisation de différentes façons.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [extension de l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="implementation"></a>Implémentation  
 Pour prendre en charge la colorisation, l’infrastructure du package managé (MPF) inclut la <xref:Microsoft.VisualStudio.Package.Colorizer>classe qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> </xref:Microsoft.VisualStudio.Package.Colorizer> Cette classe interagit avec un <xref:Microsoft.VisualStudio.Package.IScanner>pour déterminer le jeton et les couleurs.</xref:Microsoft.VisualStudio.Package.IScanner> Pour plus d’informations sur les scanneurs, voir [Analyseur de Service de langage hérité et analyseur](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer>classe, puis marque chaque caractère du jeton avec les informations de couleur et renvoie ces informations à l’éditeur d’affichage du fichier source.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 Les informations de couleur dans l’éditeur sont un index dans une liste de propriétés. Chaque élément coloriable spécifie une valeur de couleur et un jeu d’attributs de police, tels que le gras ou le barré. L’éditeur fournit un ensemble d’éléments coloriable par défaut utilisable par votre service de langage. Il vous suffit de faire est de spécifier l’index de la couleur appropriée pour chaque type de jeton. Toutefois, vous pouvez fournir un ensemble d’éléments coloriable personnalisés et les indices de que vous fournir des jetons et font référence à votre propre liste d’éléments pouvant être en couleur au lieu de la liste par défaut. Vous devez également définir le `RequestStockColors` entrée de Registre sur 0 (ou ne spécifiez pas la `RequestStockColors` entrée du tout) pour prendre en charge les couleurs personnalisées. Vous pouvez définir cette entrée de Registre avec un paramètre nommé pour la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>définis par l’utilisateur.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Pour plus d’informations sur l’inscription d’un service de langage et en définissant ses options, consultez la page [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Éléments coloriable personnalisés  
 Pour fournir vos propres éléments coloriable personnalisés, vous devez substituer <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>et <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>la méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> La première méthode retourne le nombre d’éléments coloriable personnalisés qui prend en charge de votre service de langage et la seconde Obtient l’élément coloriable personnalisé par index. Vous créez la liste par défaut des éléments coloriable personnalisés. Dans le constructeur de votre service de langage, il vous suffit fournir chaque élément coloriable avec un nom. Visual Studio exécute automatiquement le cas où l’utilisateur sélectionne un ensemble différent de propriétés. Ce nom est ce qui apparaît dans les **polices et couleurs** page de propriétés sur le **Options** boîte de dialogue (disponible à partir de Visual Studio **outils** menu) et ce nom détermine la couleur, un utilisateur a remplacé. Choix de l’utilisateur sont stockées dans un cache dans le Registre et accessible par le nom de couleur. Le **polices et couleurs** page de propriétés répertorie tous les noms de couleurs dans l’ordre alphabétique, donc vous pouvez regrouper vos couleurs personnalisées en faisant précéder chaque nom de couleur avec votre nom de langage ; par exemple, «**TestLanguage - commentaire**« et »**TestLanguage - mot clé**». Ou vous pouvez regrouper vos éléments coloriable par type, «**commentaire (TestLanguage)**« et »**(mot clé) (TestLanguage)**». Regroupement par nom de la langue est par défaut.  
  
> [!CAUTION]
>  Il est fortement recommandé d’inclure le nom du langage dans le nom de l’élément coloriable pour éviter les conflits avec des noms d’élément coloriable existants.  
  
> [!NOTE]
>  Si vous modifiez le nom d’un de vos couleurs pendant le développement, vous devez réinitialiser le cache de Visual Studio a créé la première fois que vos couleurs ont eu accès. Vous pouvez le faire en exécutant la **réinitialiser la ruche expérimentale** commande dans le menu de programme Visual Studio SDK.  
  
 Notez que le premier élément dans la liste de propriétés n’est jamais référencé. Visual Studio fournit toujours les couleurs de texte par défaut et les attributs de cet élément. Le moyen le plus simple de gérer cette situation consiste à fournir un élément coloriable espace réservé en tant que premier élément.  
  
### <a name="high-color-colorable-items"></a>Éléments coloriable de couleurs  
 Propriétés peuvent prennent également en charge les valeurs de couleur 24 bits ou élevé via la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Le MPF <xref:Microsoft.VisualStudio.Package.ColorableItem>classe prend en charge la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interface et les couleurs 24 bits sont spécifiées dans le constructeur, ainsi que les couleurs normales.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> </xref:Microsoft.VisualStudio.Package.ColorableItem> Consultez la <xref:Microsoft.VisualStudio.Package.ColorableItem>classe pour plus de détails.</xref:Microsoft.VisualStudio.Package.ColorableItem> L’exemple ci-dessous montre comment définir les couleurs 24 bits de mots-clés et commentaires. Les couleurs 24 bits sont utilisées lors de la couleur 24 bits est pris en charge sur le bureau de l’utilisateur ; Sinon, les couleurs de texte normal sont utilisées.  
  
 N’oubliez pas, que ce sont les couleurs par défaut pour votre langue ; l’utilisateur peut modifier ces couleurs à leur convenance.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre comment déclarer et remplir un tableau d’éléments coloriable personnalisés à l’aide de la <xref:Microsoft.VisualStudio.Package.ColorableItem>classe.</xref:Microsoft.VisualStudio.Package.ColorableItem> Cet exemple définit les couleurs des mots clés et les commentaires à l’aide de couleurs 24 bits.  
  
```c#  
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
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>La classe Coloriseur et l’analyseur  
 La base de <xref:Microsoft.VisualStudio.Package.LanguageService>classe a un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>méthode que la <xref:Microsoft.VisualStudio.Package.Colorizer>classe</xref:Microsoft.VisualStudio.Package.Colorizer> instantiantes</xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> Le moteur d’analyse qui est retourné à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>est passé à la méthode le <xref:Microsoft.VisualStudio.Package.Colorizer>constructeur de classe.</xref:Microsoft.VisualStudio.Package.Colorizer> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
 Vous devez implémenter la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>méthode dans votre propre version de la <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> La <xref:Microsoft.VisualStudio.Package.Colorizer>classe utilise le moteur d’analyse pour obtenir toutes les informations de couleur de jeton.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 L’analyseur a besoin pour remplir un <xref:Microsoft.VisualStudio.Package.TokenInfo>la structure de chaque jeton qu’il trouve.</xref:Microsoft.VisualStudio.Package.TokenInfo> Cette structure contient des informations telles que l’étendue du jeton occupe, l’index de la couleur à utiliser, le type est les jetons et les déclencheurs (voir <xref:Microsoft.VisualStudio.Package.TokenTriggers>).</xref:Microsoft.VisualStudio.Package.TokenTriggers> Seul l’index d’étendue et de couleur sont nécessaires pour la colorisation par la <xref:Microsoft.VisualStudio.Package.Colorizer>classe.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 L’index de couleur est stocké dans le <xref:Microsoft.VisualStudio.Package.TokenInfo>structure est généralement une valeur à partir de la <xref:Microsoft.VisualStudio.Package.TokenColor>énumération, qui fournit un certain nombre d’indices nommés correspondant aux différents éléments de langage tels que les mots clés et les opérateurs.</xref:Microsoft.VisualStudio.Package.TokenColor> </xref:Microsoft.VisualStudio.Package.TokenInfo> Si vos éléments coloriable personnalisés correspond à la liste les éléments présentés dans le <xref:Microsoft.VisualStudio.Package.TokenColor>énumération, vous pouvez simplement utiliser l’énumération comme couleur pour chaque jeton.</xref:Microsoft.VisualStudio.Package.TokenColor> Toutefois, si d’autres éléments coloriable ou si vous ne souhaitez pas utiliser les valeurs existantes dans cet ordre, vous pouvez organiser votre liste coloriable personnalisé pour répondre à vos besoins et de retourner l’index approprié dans cette liste. N’oubliez pas d’effectuer un cast de l’index vers un <xref:Microsoft.VisualStudio.Package.TokenColor>lorsque vous les stockez dans la structure <xref:Microsoft.VisualStudio.Package.TokenInfo>; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] voit uniquement l’index.</xref:Microsoft.VisualStudio.Package.TokenInfo> </xref:Microsoft.VisualStudio.Package.TokenColor>  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment l’analyseur peut identifier les trois types de jetons : nombres, signes de ponctuation et les identificateurs (tout ce qui n’est pas un nombre ou une ponctuation). Cet exemple est qu’à titre indicatif et ne représente pas une implémentation d’analyseur et moteur d’analyse complète. Il suppose qu’il existe un `Lexer` classe avec un `GetNextToken()` méthode qui retourne une chaîne.  
  
```c#  
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
 [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)
