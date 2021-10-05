# Bot-insta
Um Bot criado em Python para comentar em publicações do instagr@m, mais especificamente sorteios

Aqui tem o codigo com as explicações, recomendo roda atraves do sistema notebook igual o do arquivo.

#importa as bibliotecas previamente instaladas(selenium/webdriver)
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time
import random

#abre o navegador e o link
navegador = webdriver.Chrome()
navegador.get("https://www.instagram.com/")

time.sleep(2)

#identifica a campo de usuario
username = navegador.find_element_by_name("username")
username.clear()
time.sleep(1)

#identifica a campo de senha
password = navegador.find_element_by_xpath("//input[@name='password']")
password.clear()
time.sleep(1)

#preenche os campos
username.send_keys("user")
time.sleep(1)
password.send_keys("senha")
time.sleep(1)

#identifica e aciona o botão login
login_button = navegador.find_element_by_xpath('//*[@id="loginForm"]/div/div[3]/button')
login_button.click()
time.sleep(2)

#botão de salvar info
save_button = navegador.find_element_by_xpath('//*[@id="react-root"]/section/main/div/div/div/div/button')
save_button.click()                            
time.sleep(3)

#botao de notificação
noti_button = navegador.find_element_by_xpath('/html/body/div[5]/div/div/div/div[3]/button[2]')
noti_button.click()    

#redireciona para a publicação
navegador.get("https://www.instagram.com/p/CUQy9AklOjJ/")




#area dos comentarios
comentarios = ["@usuario", "@usuario"] #aqui vai o que será comentado, pode ser tanto uma marcação como um comentario qualquer. 
#Por enquanto vc ira precisar digitar aqui o tanto de vezes que sera comentado, e pelo metodo notebook, vc consegue executar só essa fase.

 
for sText in comentarios:              
                #identifica e clica no campo de mensagem  
                coment_space = navegador.find_element_by_class_name('Ypffh')
                navegador.find_element_by_class_name('Ypffh').click()
                time.sleep(1)
                coment_space.send_keys(sText)
                time.sleep(1)
                coment_space.send_keys(Keys.SPACE)
                time.sleep(1)
                navegador.find_element_by_xpath("//button[contains(text(), 'Publicar')]").click()
               

