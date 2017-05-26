try
                {
                    var request = (HttpWebRequest)WebRequest.Create("https://edu.grsu.by/modules/mod_metromenu/get.php");
                    
                    var postData = "action=course_save&year=2017&tn="+ user_id + "&kurs=4&block=8&code="+ code + "&name=%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B+%D0%BF%D1%80%D0%BE%D1%84%D0%B5%D1%81%D1%81%D0%B8%D0%BE%D0%BD%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%B9+%D0%BA%D0%BE%D0%BC%D0%BC%D1%83%D0%BD%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D0%B8&kotdel=3&kodsp=819&kvob=2&kvidstud=1";

                    var data = Encoding.ASCII.GetBytes(postData);

                    request.Method = "POST";
                    request.ContentType = "application/x-www-form-urlencoded";
                    request.ContentLength = data.Length;

                    using (var stream = request.GetRequestStream())
                    {
                        stream.Write(data, 0, data.Length);
                    }

                    var response = (HttpWebResponse)request.GetResponse();

                    var responseString = new StreamReader(response.GetResponseStream()).ReadToEnd();

                    dynamic returnedData = JsonConvert.DeserializeObject<dynamic>(responseString);
                    MessageBox.Show("ok");
                    

                    Thread.Sleep(500);

                }
                catch (Exception ex)
                {
                    MessageBox.Show(ex.Message);
                }
