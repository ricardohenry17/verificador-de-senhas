import re

def verificar_forca_senha(senha):
    tamanho_minimo = 8
    tem_maiuscula = bool(re.search(r'[A-Z]', senha))
    tem_minuscula = bool(re.search(r'[a-z]', senha))
    tem_numero = bool(re.search(r'[0-9]', senha))
    tem_especial = bool(re.search(r'[!@#$%^&*(),.?":{}|<>]', senha))
    
    pontuacao = 0
    recomendacoes = []

    if len(senha) >= tamanho_minimo:
        pontuacao += 1
    else:
        recomendacoes.append(f"A senha deve ter pelo menos {tamanho_minimo} caracteres.")

    if tem_maiuscula:
        pontuacao += 1
    else:
        recomendacoes.append("Adicione pelo menos uma letra maiúscula.")

    if tem_minuscula:
        pontuacao += 1
    else:
        recomendacoes.append("Adicione pelo menos uma letra minúscula.")

    if tem_numero:
        pontuacao += 1
    else:
        recomendacoes.append("Adicione pelo menos um número.")

    if tem_especial:
        pontuacao += 1
    else:
        recomendacoes.append("Adicione pelo menos um caractere especial (ex: !, @, #, $).")

    print("\n" + "="*40)
    print(" RESULTADO DA ANÁLISE DE SEGURANÇA")
    print("="*40)

    if pontuacao == 5:
        print("🟢 Senha FORTE! Excelente nível de segurança.")
    elif pontuacao >= 3:
        print("🟡 Senha MÉDIA. Pode ser melhorada.")
    else:
        print("🔴 Senha FRACA. Vulnerável a ataques.")

    if recomendacoes:
        print("\nRecomendações para melhorar:")
        for rec in recomendacoes:
            print(f" - {rec}")
    print("="*40 + "\n")

if __name__ == "__main__":
    print("=== Validador de Força de Senha (Cyber Security Tool) ===")
    user_senha = input("Digite a senha que deseja testar: ")
    verificar_forca_senha(user_senha)
