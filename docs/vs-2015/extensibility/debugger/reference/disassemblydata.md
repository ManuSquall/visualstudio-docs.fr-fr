---
title: DisassemblyData | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7904057d31d2bbc32aee060771359b85195f7d5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494934"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [DisassemblyData](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/disassemblydata).  
  
Décrit une instruction de code machine pour l’environnement de développement intégré (IDE) à afficher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>Membres  
 `dwFields`  
 Le [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) constante qui spécifie quels champs sont renseignés.  
  
 `bstrAddress`  
 L’adresse en tant qu’offset à partir d’un point de départ (généralement le début de la fonction associée).  
  
 `bstrCodeBytes`  
 Les octets de code pour cette instruction.  
  
 `bstrOpcode`  
 Le code d’opération pour cette instruction.  
  
 `bstrOperands`  
 Les opérandes pour cette instruction.  
  
 `bstrSymbol`  
 Le nom du symbole, le cas échéant, liées à l’adresse (symboles publics, étiquette et ainsi de suite).  
  
 `uCodeLocationId`  
 L’identificateur d’emplacement de code pour cette ligne désassemblée. Si l’adresse de contexte de code d’une ligne est supérieure à l’adresse de contexte de code d’un autre, puis l’identificateur d’emplacement du premier code désassemblé également sera supérieur à l’identificateur d’emplacement de code de la deuxième.  
  
 `posBeg`  
 Le [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où le code machine de données commence.  
  
 `posEnd`  
 Le [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où les données de désassemblage se terminent.  
  
 `bstrDocumentUrl`  
 Pour les documents de texte qui peuvent être représentés en tant que noms de fichiers, le `bstrDocumentUrl` champ affiche le nom du fichier où la source peut être trouvée, en utilisant le format `file://file name`.  
  
 Pour les documents de texte qui ne peut pas être représentées en tant que noms de fichiers, `bstrDocumentUrl` est un identificateur unique pour le document, et le moteur de débogage doit implémenter le [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) (méthode).  
  
 Ce champ peut contenir également des informations supplémentaires sur les sommes de contrôle. Pour plus d’informations, consultez la section Notes.  
  
 `dwByteOffset`  
 Le nombre d’octets de que l’instruction est depuis le début de la ligne de code.  
  
 `dwFlags`  
 Le [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) constante qui spécifie quels indicateurs sont actifs.  
  
## <a name="remarks"></a>Notes  
 Chaque `DisassemblyData` structure décrit une seule instruction du désassemblage. Un tableau de ces structures est retourné à partir de la [en lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) (méthode).  
  
 Le [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est utilisée pour des documents texte uniquement. La plage de code source pour cette instruction est remplie uniquement pour la première instruction générée à partir d’une instruction ou d’une ligne, par exemple, lorsque `dwByteOffset == 0`.  
  
 Pour les documents qui sont non textuelles, un contexte de document peut être obtenu à partir du code et le `bstrDocumentUrl` champ doit être une valeur null. Si le `bstrDocumentUrl` champ est le même que le `bstrDocumentUrl` champ dans le précédent `DisassemblyData` élément du tableau, puis définissez le `bstrDocumentUrl` à une valeur null.  
  
 Si le `dwFlags` champ a le `DF_DOCUMENT_CHECKSUM` l’indicateur est défini, puis les informations de somme de contrôle supplémentaires suivent la chaîne pointée par le `bstrDocumentUrl` champ. Plus précisément, après la marque de fin de chaîne null, il suit un GUID qui identifie l’algorithme de somme de contrôle qui est à son tour suivi par une valeur de 4 octets indiquant le nombre d’octets dans la somme de contrôle, qui à son tour est suivi par les octets de la somme de contrôle. Consultez l’exemple dans cette rubrique comment encoder et décoder de ce champ dans [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
## <a name="example"></a>Exemple  
 Le `bstrDocumentUrl` champ peut contenir des informations supplémentaires autres que chaîne si le `DF_DOCUMENT_CHECKSUM` indicateur est défini. Le processus de création et la lecture de cette chaîne encodée est simple dans [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]. Toutefois, dans [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], il s’agit d’un autre. Pour les curieux, l’exemple suivant montre une méthode de création de la chaîne encodée à partir de [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] et une façon de décoder la chaîne encodée dans [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [En lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

