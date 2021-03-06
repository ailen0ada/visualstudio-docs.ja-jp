---
title: DISASSEMBLY_FLAGS |Microsoft Docs
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
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85c5e4a5b0cc5dbdcff5750ce5c87d170bb9bd20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537672"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DISASSEMBLY_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/disassembly-flags)します。  
  
逆アセンブリのフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>メンバー  
 DF_DOCUMENTCHANGE  
 この命令が別のドキュメントは、前のことを示します。  
  
 DF_DISABLED  
 この命令は実行されないことを示します。  
  
 DF_INSTRUCTION_ACTIVE  
 この命令が実行される次の手順のいずれかであることを示します (あります 1 つ以上)。  
  
 DF_DATA  
 この命令は、データ (コードではなく) で、実際にあることを示します。  
  
 DF_HASSOURCE  
 この命令にソースがあることを示します。 プロファイルまたはガベージ コレクションのコードなどのいくつかの手順では、対応するソースがあるありません。  
  
 DF_DOCUMENT_CHECKSUM  
 示します`bstrDocumentUrl`フィールドには、ドキュメントの URL の後のチェックサム データが含まれています。 「解説」を参照してください、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)チェックサム データを格納する方法の構造体。  
  
## <a name="remarks"></a>Remarks  
 として使用される、`dwFlags`のメンバー、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)構造体。  
  
 これらのフラグは、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

