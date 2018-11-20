---
title: Coloration de syntaxe dans un Service de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d82a85958fd979a3d9d44375656b08356ef09d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135946"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Coloration de syntaxe dans un Service de langage hérité
Coloration de syntaxe est une fonctionnalité qui provoque des éléments d’un langage de programmation à afficher dans un fichier source dans différentes couleurs et styles. Pour prendre en charge cette fonctionnalité, vous devez fournir un analyseur ou l’analyseur qui peut identifier les types d’éléments lexicaux ou des jetons dans le fichier. De nombreux langages distinguent des mots clés, les délimiteurs (tels que des parenthèses ou d’accolades) et les commentaires en les colorisation de différentes façons.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [étendre l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="implementation"></a>Implémentation  
 Pour prendre en charge la colorisation, managed package framework (MPF) inclut le <xref:Microsoft.VisualStudio.Package.Colorizer> classe qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface. Cette classe interagit avec un <xref:Microsoft.VisualStudio.Package.IScanner> pour déterminer le jeton et les couleurs. Pour plus d’informations sur les analyseurs, consultez [Analyseur de Service de langage hérité et analyseur](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer> classe, puis marque chaque caractère du jeton avec les informations de couleur et renvoie ces informations à l’éditeur affiche le fichier source.  
  
 Les informations de couleur dans l’éditeur sont un index dans une liste de propriétés. Chaque élément coloriable spécifie une valeur de couleur et un ensemble d’attributs de police, tels que le gras ou barré. L’éditeur fournit un ensemble d’éléments coloriable par défaut utilisable par votre service de langage. Vous devez faire est de spécifier l’index de la couleur appropriée pour chaque type de jeton. Toutefois, vous pouvez fournir un ensemble d’éléments coloriable personnalisés et les indices de que vous fournissez des jetons et référencer votre propre liste d’éléments coloriable au lieu de la liste par défaut. Vous devez également définir le `RequestStockColors` entrée de Registre sur 0 (ou ne spécifiez pas la `RequestStockColors` entrée tout) pour prendre en charge les couleurs personnalisées. Vous pouvez définir cette entrée de Registre avec un paramètre nommé pour la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> définis par l’utilisateur. Pour plus d’informations sur l’inscription d’un service de langage et en définissant ses options, consultez [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Éléments coloriable personnalisés  
 Pour fournir vos propres éléments coloriable personnalisés, vous devez substituer la <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> et <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. La première méthode retourne le nombre d’éléments coloriable personnalisés qui prend en charge par votre service de langage et la seconde Obtient l’élément coloriable personnalisé par index. Vous créez la liste par défaut des éléments coloriable personnalisés. Dans le constructeur de votre service de langage, vous devez simplement fournir chaque élément coloriable avec un nom. Visual Studio gère automatiquement le cas où l’utilisateur sélectionne un ensemble différent de propriétés. Ce nom est ce qui s’affiche dans le **polices et couleurs** page de propriétés sur le **Options** boîte de dialogue (disponible à partir de Visual Studio **outils** menu) et détermine ce nom couleur d’un utilisateur a été remplacée. Choix de l’utilisateur sont stockées dans un cache dans le Registre et accessibles par le nom de couleur. Le **polices et couleurs** page de propriétés répertorie tous les noms de couleur dans l’ordre alphabétique, vous pouvez regrouper vos couleurs personnalisées en faisant précéder chaque nom de couleur de votre langue ; par exemple, «**TestLanguage - commentaire**« et »**TestLanguage - mot clé**». Ou vous pouvez regrouper vos éléments coloriable par type, «**commentaire (TestLanguage)**« et »**(mot clé) (TestLanguage)**». Regroupement par nom de la langue est par défaut.  
  
> [!CAUTION]
>  Il est fortement recommandé d’inclure le nom du langage dans le nom de l’élément coloriable pour éviter les conflits avec des noms d’élément coloriable existants.  
  
> [!NOTE]
>  Si vous modifiez le nom de l’un de vos couleurs pendant le développement, vous devez réinitialiser le cache de Visual Studio a créé la première fois que les couleurs ont été accédés. Vous pouvez le faire en exécutant la **réinitialiser la ruche expérimentale** commande dans le menu du programme Visual Studio SDK.  
  
 Notez que le premier élément dans votre liste de propriétés n’est jamais référencé. Visual Studio fournit toujours les couleurs de texte par défaut et les attributs de cet élément. Des solutions à ce problème, le plus simple consiste à fournir un élément coloriable d’espace réservé en tant que le premier élément.  
  
### <a name="high-color-colorable-items"></a>Éléments coloriable de couleurs  
 Éléments coloriable peuvent prennent également en charge les valeurs de couleur 24 bits ou élevé à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> classe prend en charge la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface et les couleurs 24 bits sont spécifiées dans le constructeur, ainsi que les couleurs normales. Pour plus d'informations, consultez la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. L’exemple ci-dessous montre comment définir les couleurs 24 bits pour les mots clés et des commentaires. Les couleurs 24 bits sont utilisés lors de la couleur 24 bits est pris en charge sur le bureau de l’utilisateur ; Sinon, les couleurs de texte normal sont utilisés.  
  
 N’oubliez pas, que ce sont les couleurs par défaut pour votre langue ; l’utilisateur peut modifier ces couleurs à leur convenance.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre une manière à déclarer et remplir un tableau d’éléments de coloriable personnalisés à l’aide de la <xref:Microsoft.VisualStudio.Package.ColorableItem> classe. Cet exemple définit les couleurs des mots clés et des commentaires à l’aide de couleurs 24 bits.  
  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>La classe Coloriseur et l’analyseur  
 La base de <xref:Microsoft.VisualStudio.Package.LanguageService> classe a un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> méthode ce instantiantes la <xref:Microsoft.VisualStudio.Package.Colorizer> classe. L’analyseur est retourné à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> est passé à la méthode le <xref:Microsoft.VisualStudio.Package.Colorizer> constructeur de classe.  
  
 Vous devez implémenter la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode dans votre propre version de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilise le moteur d’analyse pour obtenir toutes les informations de jeton de couleur.  
  
 L’analyseur a besoin pour remplir un <xref:Microsoft.VisualStudio.Package.TokenInfo> structure pour chaque jeton de recherche. Cette structure contient des informations telles que l’étendue du jeton occupe, l’index de la couleur à utiliser, le type est les déclencheurs de jetons et de jetons (voir <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Seul l’index d’étendue et de couleur sont nécessaires pour la colorisation par la <xref:Microsoft.VisualStudio.Package.Colorizer> classe.  
  
 L’index de couleur est stocké dans le <xref:Microsoft.VisualStudio.Package.TokenInfo> structure est généralement une valeur à partir de la <xref:Microsoft.VisualStudio.Package.TokenColor> énumération, qui fournit un certain nombre d’indices nommées correspondant aux différents éléments de langage tels que les mots clés et les opérateurs. Si vos éléments coloriable personnalisés liste des correspondances les éléments présentés dans le <xref:Microsoft.VisualStudio.Package.TokenColor> énumération, puis vous pouvez simplement utiliser l’énumération comme couleur pour chaque jeton. Toutefois, si vous avez d’autres éléments coloriable ou que vous ne souhaitez pas utiliser les valeurs existantes dans l’ordre, vous pouvez organiser votre liste coloriable personnalisé pour répondre à vos besoins et de retourner l’index approprié dans cette liste. Veillez à effectuer un cast de l’index à un <xref:Microsoft.VisualStudio.Package.TokenColor> lors du stockage dans le <xref:Microsoft.VisualStudio.Package.TokenInfo> structure ; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] voit uniquement l’index.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment l’analyseur peut identifier les trois types de jetons : nombres, signes de ponctuation et les identificateurs (tout ce qui n’est pas un nombre ou un signe de ponctuation). Cet exemple est à titre d’illustration uniquement et ne représente pas une implémentation complète de l’analyseur et l’Analyseur de. Il suppose qu’il existe un `Lexer` classe avec un `GetNextToken()` méthode qui retourne une chaîne.  
  
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
 [Fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)   
 [Analyseur et l’Analyseur de Service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)