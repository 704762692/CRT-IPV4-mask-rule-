# $language = "Python"
# $interface = "1.0"
from itertools import combinations


#输入协议号和掩码
proto = crt.Dialog.Prompt("Please fill in the proto","poror","",0)
proto_mask = crt.Dialog.Prompt("Please fill in the proto-mask","proto-mask","",0)
a=proto+' '+proto_mask

#输入源ip和掩码
sip = crt.Dialog.Prompt("Please fill in the sip","sip","",0)
sip_mask = crt.Dialog.Prompt("Please fill in the sip-mask","sip-mask","",0)
b=sip+' '+sip


#输入源端口和掩码
sport = crt.Dialog.Prompt("Please fill in the sport","sport","",0)
sport_mask = crt.Dialog.Prompt("Please fill in the sport-mask","sport-mask","",0)
c=sport+' '+sport_mask

#输入目标ip和掩码
dip = crt.Dialog.Prompt("Please fill in the dip","dip","",0)
dip_mask = crt.Dialog.Prompt("Please fill in the dip-mask","dip-mask","",0)
d=dip+' '+dip_mask

#输入目标端口和掩码
dport  = crt.Dialog.Prompt("Please fill in the dport ","dport ","",0)
dport_mask = crt.Dialog.Prompt("Please fill in the dport -mask","dport -mask","",0)
e=dport +' '+dport_mask


rule=[a,b,c,d,e]
for i in range(0,6):
    for x in combinations(range(5),i):
        j=len(x)
        for k in range(j):
            count=x[k]
            rule[count]='any'
        if rule[1] != rule[3]:
            rule_str=('ipv4-mask rule match'+' '+rule[0]+' '+rule[1]+' '+rule[2]+' '+rule[3]+' '+rule[4]+' '+'apply service 0')
            crt.Screen.Send(rule_str)
            crt.Screen.Send("\r\n")
        rule= [a, b, c, d, e]
