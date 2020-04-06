---
title: Prise en charge des extraits de code dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704913"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Prise en charge des extraits de code dans un service de langage hérité
Un extrait de code est un morceau de code qui est inséré dans le fichier source. L’extrait lui-même est un modèle basé sur XML avec un ensemble de champs. Ces champs sont mis en évidence après l’extrait est inséré et peuvent avoir des valeurs différentes en fonction du contexte dans lequel l’extrait est inséré. Immédiatement après l’extrait est inséré, le service linguistique peut formater l’extrait.

 L’extrait est inséré dans un mode d’édition spécial qui permet de naviguer dans les champs de l’extrait à l’aide de la clé TAB. Les champs peuvent prendre en charge les menus d’abandon de style IntelliSense. L’utilisateur commet l’extrait au fichier source en tapant soit la clé ENTER ou la clé ESC. Pour en savoir plus sur les extraits, veuillez consulter [Code Snippets](../../ide/code-snippets.md).

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Procédure Pas à pas : Mise en œuvre de Snippets de code](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="managed-package-framework-support-for-code-snippets"></a>Support cadre de paquet géré pour les extraits de code
 Le cadre de paquet géré (MPF) prend en charge la plupart des fonctionnalités d’extrait, de la lecture du modèle à l’insertion de l’extrait et permettant le mode d’édition spéciale. Le support est <xref:Microsoft.VisualStudio.Package.ExpansionProvider> géré par la classe.

 Lorsque <xref:Microsoft.VisualStudio.Package.Source> la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> classe est instantanée, la <xref:Microsoft.VisualStudio.Package.LanguageService> méthode de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe est appelée <xref:Microsoft.VisualStudio.Package.LanguageService> pour obtenir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> un objet <xref:Microsoft.VisualStudio.Package.Source> (notez que la classe de base renvoie toujours un nouvel objet pour chaque objet).

 Le MPF ne prend pas en charge les fonctions d’expansion. Une fonction d’expansion est une fonction nommée qui est intégrée dans un modèle d’extrait et retourne une ou plusieurs valeurs à placer dans un champ. Les valeurs sont retournées par <xref:Microsoft.VisualStudio.Package.ExpansionFunction> le service linguistique lui-même à travers un objet. L’objet <xref:Microsoft.VisualStudio.Package.ExpansionFunction> doit être mis en œuvre par le service linguistique pour prendre en charge les fonctions d’expansion.

## <a name="providing-support-for-code-snippets"></a>Fournir un soutien aux extraits de code
 Pour permettre le support pour les extraits de code, vous devez fournir ou installer les extraits et vous devez fournir les moyens pour l’utilisateur d’insérer ces extraits. Il y a trois étapes pour permettre le support pour les extraits de code :

1. Installation des fichiers extraits.

2. Activer des extraits de code pour votre service linguistique.

3. Invoquer <xref:Microsoft.VisualStudio.Package.ExpansionProvider> l’objet.

### <a name="installing-the-snippet-files"></a>Installation des fichiers Snippet
 Tous les extraits d’une langue sont stockés sous forme de modèles dans les fichiers XML, généralement un modèle d’extrait par fichier. Pour plus de détails sur le schéma XML utilisé pour les modèles d’extrait de code, voir [Code Snippets Schema Reference](../../ide/code-snippets-schema-reference.md). Chaque modèle d’extrait est identifié avec une pièce d’identité linguistique. Cette pièce d’identité est spécifiée `Language` dans le \<registre et est mise dans l’attribut du Code> tag dans le modèle.

 Il y a généralement deux endroits où les fichiers de modèle d’extrait sont stockés : 1) où votre langue a été installée et 2) dans le dossier de l’utilisateur. Ces emplacements sont ajoutés au registre afin que le Visual Studio **Code Snippets Manager** puisse trouver les extraits. Le dossier de l’utilisateur est l’endroit où les extraits créés par l’utilisateur sont stockés.

 La disposition typique du dossier pour les fichiers de modèles d’extraits installés ressemble à ceci :\\ *[InstallRoot]*\\ *[TestLanguage]*'Snippets *[LCID]*'Snippets.

 *[InstallRoot]* est le dossier dans lequel votre langue est installée.

 *[TestLanguage]* est le nom de votre langue comme nom de dossier.

 *[LCID]* est l’ID local. C’est ainsi que les versions localisées de vos extraits sont stockées. Par exemple, l’ID local pour l’anglais est 1033, donc *[LCID]* est remplacé par 1033.

 Un fichier supplémentaire doit être fourni et c’est un fichier index, généralement appelé SnippetsIndex.xml ou ExpansionsIndex.xml (vous pouvez utiliser n’importe quel nom de fichier valide se terminant en .xml). Ce fichier est généralement stocké dans le dossier\\ *[InstallRoot] [TestLanguage]* et spécifie l’emplacement exact du dossier de extraits ainsi que l’ID de langue et le GUID du service linguistique qui utilise les extraits. *[InstallRoot]* La trajectoire exacte du fichier de l’index est mise dans le registre comme décrit plus tard dans « Installer les inscriptions au registre ». Voici un exemple d’un fichier SnippetsIndex.xml:

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 L’étiquette \<Language> spécifie l’ID de langue (l’attribut) `Lang` et le service linguistique GUID.

 Cet exemple suppose que vous avez installé votre service linguistique dans le dossier d’installation Visual Studio. Le %LCID% est remplacé par l’ID local actuel de l’utilisateur. Plusieurs \<étiquettes SnippetDir> peuvent être ajoutées, une pour chaque répertoire et lieu différents. En outre, un dossier d’extrait peut contenir des sous-plieurs, dont \<chacun est identifié dans le fichier index avec l’étiquette de> SnippetSubDir qui est incorporé dans une \<étiquette de> SnippetDir.

 Les utilisateurs peuvent également créer leurs propres extraits pour votre langue. Ceux-ci sont généralement stockés dans le dossier de paramètres de l’utilisateur, par exemple *[TestDocs]*'Code Snippets\\ *[TestLanguage]*'Test Code Snippets, où *[TestDocs]* est l’emplacement du dossier de paramètres de l’utilisateur pour Visual Studio.

 Les éléments de substitution suivants peuvent être \<placés dans le chemin stocké dans l’étiquette DirPath> dans le fichier d’index.

|Élément|Description|
|-------------|-----------------|
|%LCID%|ID de paramètres régionaux.|
|%InstallRoot%|Dossier d’installation racine pour Visual Studio, par exemple, C: 'Program Files’Microsoft Visual Studio 8.|
|%ProjDir%|Dossier contenant le projet en cours.|
|%ProjItem%|Dossier contenant l’élément de projet actuel.|
|%TestDocs%|Dossier dans le dossier de paramètres de l’utilisateur, par\\exemple, C: 'Documents et Paramètres *[nom d’utilisateur]*'Mes Documents’Visual Studio'8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Activer les extraits de code pour votre service linguistique
 Vous pouvez activer des extraits de code <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> pour votre service linguistique en ajoutant l’attribut à votre VSPackage (voir [Enregistrement d’un service de langue héritée](../../extensibility/internals/registering-a-legacy-language-service1.md) pour plus de détails). Les <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> paramètres et les paramètres sont `SearchPaths` facultatifs, mais vous devez inclure le paramètre désigné afin d’informer le **gestionnaire de code Snippets** de l’emplacement de vos extraits.

 Voici un exemple de la façon d’utiliser cet attribut :

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Appel au fournisseur d’expansion
 Le service linguistique contrôle l’insertion de tout extrait de code, ainsi que la façon dont l’insertion est invoquée.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Appel au fournisseur d’expansion pour les extraits de code
 Il existe deux façons d’invoquer le fournisseur d’expansion : en utilisant une commande de menu ou en utilisant un raccourci d’une liste d’achèvement.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Insertion d’un extrait de code à l’aide d’une commande de menu
 Pour utiliser une commande de menu pour afficher le navigateur extrait, <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> vous ajoutez <xref:Microsoft.VisualStudio.Package.ExpansionProvider> une commande de menu, puis appelez la méthode dans l’interface en réponse à cette commande de menu.

1. Ajoutez une commande et un bouton à votre fichier .vsct. Vous pouvez trouver des instructions pour le faire dans [la création d’une extension avec une commande de menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dérivez une <xref:Microsoft.VisualStudio.Package.ViewFilter> classe de la <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> classe et remplacez la méthode pour indiquer le soutien à la nouvelle commande de menu. Cet exemple permet toujours la commande du menu.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. Remplacer la <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> méthode <xref:Microsoft.VisualStudio.Package.ViewFilter> de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe pour <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> obtenir l’objet et appeler la méthode sur cet objet.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     Les méthodes suivantes <xref:Microsoft.VisualStudio.Package.ExpansionProvider> dans la classe sont appelées par Visual Studio dans l’ordre donné pendant le processus d’insertion de l’extrait:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Une <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> fois la méthode appelée, l’extrait a <xref:Microsoft.VisualStudio.Package.ExpansionProvider> été inséré et l’objet est dans un mode de modification spécial utilisé pour modifier un extrait qui vient d’être inséré.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Insertion d’un extrait de code à l’aide d’un raccourci
 La mise en œuvre d’un raccourci à partir d’une liste d’achèvement est beaucoup plus impliquée que la mise en œuvre d’une commande de menu. Vous devez d’abord ajouter des raccourcis d’extrait à la liste d’achèvement des mots IntelliSense. Ensuite, vous devez détecter quand un nom de raccourci extrait a été inséré à la suite de l’achèvement. Enfin, vous devez obtenir le titre et le chemin de l’extrait <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> en utilisant <xref:Microsoft.VisualStudio.Package.ExpansionProvider> le nom de raccourci et transmettre cette information à la méthode sur la méthode.

 Pour ajouter des raccourcis d’extrait au mot liste <xref:Microsoft.VisualStudio.Package.Declarations> d’achèvement, ajoutez-les à l’objet de votre <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Vous devez vous assurer que vous pouvez identifier le raccourci comme un nom extrait. Par exemple, voir [Procédure pas à pas : obtenir une liste de Snippets de code installés (Legacy Implementation)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Vous pouvez détecter l’insertion du raccourci d’extrait de code dans la <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Étant donné que le nom de l’extrait a déjà été inséré dans le fichier source, il doit être supprimé lorsque l’expansion est insérée. La <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> méthode prend une travée qui décrit le point d’insertion pour l’extrait; si la portée comprend l’ensemble du nom extrait dans le fichier source, ce nom est remplacé par l’extrait.

 Voici une version <xref:Microsoft.VisualStudio.Package.Declarations> d’une classe qui gère l’insertion d’extraits donné un nom de raccourci. D’autres <xref:Microsoft.VisualStudio.Package.Declarations> méthodes de la classe ont été omises pour plus de clarté. Notez que le constructeur de <xref:Microsoft.VisualStudio.Package.LanguageService> cette classe prend un objet. Cela peut être transmis à <xref:Microsoft.VisualStudio.Package.AuthoringScope> partir de votre version de <xref:Microsoft.VisualStudio.Package.AuthoringScope> l’objet <xref:Microsoft.VisualStudio.Package.LanguageService> (par exemple, votre mise en `TestDeclarations` œuvre de la classe peut prendre l’objet dans son constructeur et transmettre cet objet à votre constructeur de classe).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Lorsque le service linguistique obtient le nom <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> de raccourci, il appelle la méthode pour obtenir le nom de fichier et le titre d’extrait de code. Le service de <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> langue appelle <xref:Microsoft.VisualStudio.Package.ExpansionProvider> alors la méthode dans la classe pour insérer l’extrait de code. Les méthodes suivantes sont appelées par Visual <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Studio dans l’ordre donné dans la classe pendant le processus d’insertion de l’extrait:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Pour plus d’informations sur l’obtention d’une liste de extraits de code installé pour votre service linguistique, voir [Procédure Pas à pas: Obtenir une liste de Snippets de code installé (Legacy Implementation)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Mise en œuvre de la classe ExpansionFunction
 Une fonction d’expansion est une fonction nommée qui est intégrée dans un modèle d’extrait et retourne une ou plusieurs valeurs à placer dans un champ. Afin de prendre en charge les fonctions d’expansion <xref:Microsoft.VisualStudio.Package.ExpansionFunction> de votre <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> service linguistique, vous devez tirer une classe de la classe et mettre en œuvre la méthode. Vous devez ensuite <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> passer outre <xref:Microsoft.VisualStudio.Package.LanguageService> à la méthode de la classe <xref:Microsoft.VisualStudio.Package.ExpansionFunction> pour retourner une nouvelle instantanéisation de votre version de la classe pour chaque fonction d’expansion que vous soutenez. Si vous soutenez une liste de valeurs possibles à <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> partir d’une fonction d’expansion, vous devez également passer outre à la méthode de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe pour retourner une liste de ces valeurs.

 Une fonction d’expansion qui prend des arguments ou doit accéder à d’autres champs ne devrait pas être associée à un champ modifiable, car le fournisseur d’expansion pourrait ne pas être entièrement initialisé au moment où la fonction d’expansion est appelée. Par conséquent, la fonction d’expansion n’est pas en mesure d’obtenir la valeur de ses arguments ou de tout autre domaine.

### <a name="example"></a>Exemple
 Voici un exemple de la façon `GetName` dont une fonction d’expansion simple appelée pourrait être implémentée. Cette fonction d’expansion appendice un numéro à un nom de classe de base chaque fois que la fonction d’expansion est instantanée (ce qui correspond à chaque fois que l’extrait de code associé est inséré).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>Voir aussi
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Code Snippets](../../ide/code-snippets.md)
- [Procédure pas à pas : obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
