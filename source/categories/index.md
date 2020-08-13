---
title: 算法
date: 2020-07-09 17:57:28
type: "categories"
---
import java.math.BigInteger;

public class Demo {
	public static void main(String[] args) {
		String str="245abcdksl";
		BigInteger n=encyp(str);
		String s=decode(n);
		System.out.println(n.toString()+" "+s);
	}
	public static BigInteger encyp(String s) {
		BigInteger n=BigInteger.ZERO;
		for(int i=0;i<s.length();i++) {
			//n=n*256+s.charAt(i);
			n=n.multiply(BigInteger.valueOf(256)).add(BigInteger.valueOf(s.charAt(i)));
		}
		return n;
	}
	public static String decode(BigInteger n) {
		StringBuilder sb=new StringBuilder();
		while(n.compareTo(BigInteger.ZERO)==1) {
			for(int i=0;i<256;i++) {
//				if((n-i)%256==0) {
//					sb.append((char)i);
//					n=n-i;
//					n=n/256;
//					break;
//				}
				if((n.subtract(BigInteger.valueOf(i))).mod(BigInteger.valueOf(256)).equals(BigInteger.ZERO)) {
					sb.append((char)i);
					n=n.subtract(BigInteger.valueOf(i));
					n=n.divide(BigInteger.valueOf(256));
					break;
				}
			}
		}
		return sb.reverse().toString();
	}

}
