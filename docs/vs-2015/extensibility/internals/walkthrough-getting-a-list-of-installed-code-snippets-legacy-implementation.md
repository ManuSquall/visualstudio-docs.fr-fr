---
title: 'Procédure pas à pas : Obtention d’une liste d’installé des extraits de Code (implémentation héritée) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef16552fbbb051a24d7b2e1fbe5b5266774ef13f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949729"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Procédure pas à pas : obtention d’une liste d’extraits de code installés (implémentation héritée)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un extrait de code est un morceau de code qui peut être insérée dans la mémoire tampon source avec une commande de menu (ce qui permet de choisir parmi une liste d’extraits de code installé) ou en sélectionnant un raccourci d’extrait de code à partir d’une liste de saisie semi-automatique IntelliSense.  
  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> méthode obtient tous les extraits de code pour une langue spécifique GUID. Les raccourcis pour ces extraits de code peuvent être insérées dans une liste de saisie semi-automatique IntelliSense.  
  
 Consultez [prise en charge des extraits de Code dans un Service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) pour plus d’informations sur l’implémentation des extraits de code dans un service de langage de package gérée framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Pour récupérer une liste d’extraits de code  
  
1.  Le code suivant montre comment obtenir la liste des extraits de code pour une langue donnée. Les résultats sont stockés dans un tableau de <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> structures. Cette méthode utilise la méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> méthode pour obtenir le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> de l’interface à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> service. Toutefois, vous pouvez également utiliser le fournisseur de services donné à votre VSPackage et l’appel de la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> (méthode).  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Pour appeler la méthode GetSnippets  
  
1.  La méthode suivante montre comment appeler le `GetSnippets` méthode à la fin d’une opération d’analyse. Le <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> méthode est appelée après une opération d’analyse qui a été démarrée avec la raison <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  Le `expansionsList` listis mis en cache pour des raisons de performances de tableau. Modifications pour les extraits de code ne sont pas répercutées dans la liste jusqu'à ce que le service de langage est arrêté et rechargé (par exemple, en arrêtant et redémarrant [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Pour utiliser les informations de l’extrait de code  
  
1.  Le code suivant montre comment utiliser les informations de l’extrait de code retournées par le `GetSnippets` (méthode). Le `AddSnippets` méthode est appelée à partir de l’analyseur en réponse à une raison quelconque, l’analyse est utilisée pour remplir une liste d’extraits de code. Cela doit avoir lieu après que l’analyse complète a été effectuée pour la première fois.  
  
     Le `AddDeclaration` méthode génère une liste des déclarations qui est ensuite affichée dans une liste de saisie semi-automatique.  
  
     Le `TestDeclaration` classe contient toutes les informations qui peuvent être affichées dans une liste de saisie semi-automatique, ainsi que le type de déclaration.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
