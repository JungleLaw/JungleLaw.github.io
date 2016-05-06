package com.zte.test;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class TestSeverlet extends HttpServlet {
	@Override
	protected void doGet(HttpServletRequest req, HttpServletResponse resp)
			throws ServletException, IOException {
		String myname = req.getParameter("myname");
		resp.setCharacterEncoding("UTF-8");
		String jsonStr = "{\"name\":\"" + myname + "\",\"type\":\"虫子\"}";
		resp.setContentType("text/json; charset=UTF-8");
		if (myname != null && !myname.isEmpty()) {
			System.out.println(jsonStr);
		} else {
			System.out.println("doGet " + count++);
		}
		PrintWriter out = resp.getWriter();
		out.println(jsonStr);// 利用PrintWriter对象的方法将数据发送给客户端 　　
		out.close();
	}

	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse resp)
			throws ServletException, IOException {
		// TODO Auto-generated method stub
		super.doPost(req, resp);
		System.out.println("doPost");
	}

	private long count = 0;

	@Override
	public void init() throws ServletException {
		// TODO Auto-generated method stub
		super.init();
	}
}
