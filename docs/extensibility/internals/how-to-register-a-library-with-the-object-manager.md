---
title: 'Comment : inscrire une bibliothèque avec le Gestionnaire d’objets | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61976fbc63efd4c15e5ed88a159ea8e73bdf38f3
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513320"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Comment : inscrire une bibliothèque avec le Gestionnaire d’objets
Exploration des symboles d’outils, tels que **affichage de classes**, **Explorateur d’objets**, **Explorateur d’appels** et **résultats**, vous permettent d’afficher symboles dans votre projet ou dans des composants externes. Les symboles incluent des espaces de noms, classes, interfaces, méthodes et autres éléments de langage. Les bibliothèques de suivre ces symboles et les exposer à le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets qui remplit les outils avec les données.  
  
 Le Gestionnaire d’objets effectue le suivi de toutes les bibliothèques disponibles. Chaque bibliothèque doit inscrire avec le Gestionnaire d’objets avant de fournir les symboles pour les outils de recherche de symboles.  
  
 En règle générale, vous inscrivez une bibliothèque lors de la charge d’un VSPackage. Toutefois, il est possible à un autre moment en fonction des besoins. Vous annulez l’inscription de la bibliothèque lorsque le package Visual Studio s’arrête.  
  
 Pour inscrire une bibliothèque, utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> (méthode). Pour une bibliothèque de code managé, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (méthode).  
  
 Pour annuler l’inscription d’une bibliothèque, utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> (méthode).  
  
 Pour obtenir une référence pour le Gestionnaire d’objets, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, transmettez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID de service `GetService` (méthode).  
  
## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Inscrire et annuler l’inscription d’une bibliothèque avec le Gestionnaire d’objets  
  
### <a name="to-register-a-library-with-the-object-manager"></a>Pour inscrire une bibliothèque avec le Gestionnaire d’objets  
  
1.  Créer une bibliothèque.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Obtenir une référence à un objet de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tapez, puis appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (méthode).  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
### <a name="to-unregister-a-library-with-the-object-manager"></a>Pour annuler l’inscription d’une bibliothèque avec le Gestionnaire d’objets  
  
1.  Obtenir une référence à un objet de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tapez, puis appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> (méthode).  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Prend en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Comment : exposer des listes de symboles fournis par la bibliothèque pour le Gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)