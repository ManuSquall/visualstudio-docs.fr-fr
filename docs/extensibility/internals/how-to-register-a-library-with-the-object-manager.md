---
title: "Comment : inscrire une biblioth&#232;que avec le Gestionnaire d&#39;objets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bibliothèques, l'inscription auprès de gestionnaire d'objets"
  - "Interface IVsLibrary2, enregistrement de la bibliothèque avec le Gestionnaire d'objets"
  - "Interface IVsSimpleLibrary2, enregistrement de la bibliothèque avec le Gestionnaire d'objets"
  - "Interface IVsObjectManager2, enregistrement de la bibliothèque avec le Gestionnaire d'objets"
  - "bibliothèques, outils de consultation du symbole"
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment : inscrire une biblioth&#232;que avec le Gestionnaire d&#39;objets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

les outils de Symbole\-navigation, tels qu' **Affichage de classes**, **Explorateur d'objets**, **Explorateur d'appels** et **Résultats de la recherche de symbole**, vous permettent d'afficher des symboles dans votre projet ou dans les composants externes.  Les symboles incluent des espaces de noms, des classes, des interfaces, des méthodes, et d'autres éléments de langage.  Les bibliothèques suivent ces symboles et exposent au gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui remplit outils avec les données.  
  
 Le gestionnaire d'objets conserve toutes les bibliothèques disponibles.  Chaque bibliothèque doit s'inscrire le gestionnaire d'objets avant de fournir les symboles pour les outils de symbole\-navigation.  
  
 En général, vous enregistrez une bibliothèque lorsqu'un VSPackage charge.  Toutefois, il peut être établie vers une autre heure si nécessaire.  Vous annulez l'inscription de la bibliothèque lorsque le VSPackage arrête.  
  
 Pour inscrire une bibliothèque, utilisez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> .  dans le cas de la bibliothèque de code managé, utilisez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  
  
 Pour annuler l'enregistrement d'une bibliothèque, utilisez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .  
  
 Pour obtenir une référence au gestionnaire d'objets, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passez l'ID de service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> à la méthode d' `GetService` .  
  
## Enregistrer et d'annuler l'inscription une bibliothèque avec le gestionnaire d'objets  
  
#### Pour inscrire une bibliothèque avec le gestionnaire d'objets  
  
1.  créez une bibliothèque.  
  
    ```vb#  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```c#  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Obtenir une référence à un objet du type d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> et appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  
  
    ```vb#  
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
  
    ```c#  
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
  
#### Pour annuler l'enregistrement d'une bibliothèque avec le gestionnaire d'objets  
  
1.  Obtenir une référence à un objet du type d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> et appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .  
  
    ```vb#  
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
  
    ```c#  
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
  
## Voir aussi  
 [Extensibilité du Service de langage ancien](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Prise en charge d'outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Comment : exposer de listes de symboles fournis par la bibliothèque pour le Gestionnaire d'objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)